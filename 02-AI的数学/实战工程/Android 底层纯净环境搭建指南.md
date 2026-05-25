---
tags:
  - Android
  - PyTorch
  - Environment
  - C++
  - 交叉编译
title: PyTorch移动端部署：Android底层纯净环境搭建指南
date: {{date}}
---

# PyTorch Mobile 部署：Android 底层纯净环境搭建指南

> [!abstract] 核心工程原则
> 1. **物理隔离**：IDE 安装路径、SDK 工具链路径、个人项目代码路径必须三者严格分离。
> 2. **路径洁癖**：全程**绝对禁止**出现中文或空格（彻底规避底层 C++ (NDK/CMake) 交叉编译时的乱码和路径截断报错）。
> 3. **状态可控**：遇错不盲目依赖 IDE 界面排查，优先执行物理级缓存清理，恢复环境“真空状态”。

---

## 零、 环境重启与物理清理（可选/排错用）
> [!warning] 警告
> 当遭遇不明原因的 Gradle 同步失败或 JNI 编译报错时，执行此步骤彻底抹除毒缓存。

1. **全局构建缓存**：删除 `C:\Users\<用户名>\.gradle` 文件夹。
2. **残缺 SDK**：直接删除旧的 `Sdk` 文件夹。
3. **项目局部缓存**：删除项目根目录下的 `.idea/`、`.gradle/`、`build/` 以及 `app/build/`。

---

## 一、 核心 IDE 安装与初始化

1. **下载纯净包**：从 Android 开发者中国官网下载最新版 Android Studio。
2. **自定义安装路径**：
   - 绝不使用默认的 `C:\Program Files`。
   - 设定独立干净路径，例如：`E:\and_ai`。
3. **首次启动初始化 (Setup Wizard)**：
   - 弹窗选择 **"Do not import settings"**（不导入旧设置）。
   - Setup Type 选择 **"Custom" (自定义)**。
   - **重定向 SDK 路径**：在向导中将 SDK 路径修改为独立目录，例如：`D:\and_sdk`。
   - 接受所有许可协议 (Accept) 并等待核心组件下载完成。

---

## 二、 注入 C++ 交叉编译大脑 (PyTorch 核心依赖)
> [!info] 原理
> PyTorch Mobile 底层由 C++ 编写 (LibTorch)。手机芯片多为 ARM 架构，电脑为 x86 架构。必须通过 NDK 将 C++ 代码交叉编译为手机能看懂的 `.so` 动态链接库。

1. 在 Android Studio 欢迎界面，点击 **More Actions -> SDK Manager**。
2. 切换到中间的 **SDK Tools** 标签页。
3. 勾选并下载以下两项核心底层工具：
   - **`NDK (Side by side)`**：C/C++ 交叉编译核心工具链。
   - **`CMake`**：C/C++ 自动化构建与调度中枢。
4. 点击 Apply，等待下载解压完成。

---

## 三、 创建底层验证沙盒 (第一个项目)

1. 在欢迎界面点击 **New Project**。
2. 模板选择：**Empty Views Activity**（使用经典 XML 视图，避免引入 Compose 框架的复杂性）。
3. **关键参数配置**：
   - **Name**: `first_ai_project`
   - **Package name**: `com.example.first_ai_project`
   - **Save location**: 设定一个全新的、独立于 IDE 和 SDK 之外的纯净路径，例如：`E:\MyAndroidProjects\first_ai_project`。
   - **Language**: Java / Kotlin
   - **Minimum SDK**: API 24 (Android 7.0)
   - **Build configuration language**: Groovy DSL (build.gradle)
4. 点击 Finish，静待底部 Gradle 进度条跑完。当左侧目录树清晰呈现（包含 `app`, `src`, `main`）且无报错时，环境闭环打通。