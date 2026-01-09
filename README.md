<!DOCTYPE html>
<html lang="zh-CN">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>UrKnows 插件使用指南 | AI 驱动的智能代码文档生成工具</title>
    
    <!-- SEO Meta Tags -->
    <meta name="description" content="UrKnows 是一个强大的 AI 驱动代码文档生成工具，支持 VSCode、Cursor、Qoder 等编辑器。自动生成代码文档、技术文档、项目文档，支持 Wiki 格式、Markdown 格式，提供可视化配置、任务管理、文档预览和 Claude Skills 导出功能。">
    <meta name="keywords" content="UrKnows,代码文档生成,AI文档生成,代码文档工具,VSCode插件,Cursor插件,代码Wiki,技术文档生成,项目文档,代码文档化,文档自动生成,代码分析工具,文档生成器,代码文档系统,开发文档,API文档生成,代码库文档,文档工具,代码注释生成,文档生成插件,Wiki生成,Markdown文档,Claude Skills,代码文档化工具,智能文档生成,代码文档管理,文档预览,代码文档系统,开发工具,编程文档">
    <meta name="author" content="UrKnows Team">
    <meta name="robots" content="index, follow">
    <meta name="language" content="zh-CN">
    
    <!-- Open Graph / Facebook -->
    <meta property="og:type" content="website">
    <meta property="og:title" content="UrKnows 插件使用指南 | AI 驱动的智能代码文档生成工具">
    <meta property="og:description" content="UrKnows 是一个强大的 AI 驱动代码文档生成工具，支持 VSCode、Cursor、Qoder 等编辑器。自动生成代码文档、技术文档、项目文档，支持 Wiki 格式、Markdown 格式。">
    <meta property="og:site_name" content="UrKnows">
    
    <!-- Twitter -->
    <meta name="twitter:card" content="summary_large_image">
    <meta name="twitter:title" content="UrKnows 插件使用指南 | AI 驱动的智能代码文档生成工具">
    <meta name="twitter:description" content="UrKnows 是一个强大的 AI 驱动代码文档生成工具，支持 VSCode、Cursor、Qoder 等编辑器。自动生成代码文档、技术文档、项目文档。">
    
    <!-- Canonical URL -->
    <link rel="canonical" href="https://github.com/2hangchen/urknows">
    
    <!-- Tailwind CSS -->
    <script src="https://cdn.tailwindcss.com"></script>
    <!-- Font Awesome 图标 -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.1/css/all.min.css">
    <!-- 自定义 Tailwind 配置 -->
    <script>
        tailwind.config = {
            darkMode: 'class',
            theme: {
                extend: {
                    colors: {
                        primary: '#007acc', // VSCode 主色调
                        secondary: '#61dafb', // React 蓝（辅助色）
                        dark: {
                            bg: '#1e1e1e',
                            card: '#252526',
                            text: '#e0e0e0'
                        },
                        light: {
                            bg: '#f8f9fa',
                            card: '#ffffff',
                            text: '#212529'
                        }
                    },
                    fontFamily: {
                        sans: ['Inter', 'system-ui', 'sans-serif'],
                        mono: ['Fira Code', 'Consolas', 'monospace']
                    },
                    animation: {
                        'pulse-slow': 'pulse 3s cubic-bezier(0.4, 0, 0.6, 1) infinite',
                    }
                }
            }
        }
    </script>
    <style type="text/tailwindcss">
        @layer utilities {
            .content-auto {
                content-visibility: auto;
            }
            .text-shadow {
                text-shadow: 0 2px 4px rgba(0,0,0,0.1);
            }
            .card-hover {
                @apply transition-all duration-300 hover:shadow-lg hover:-translate-y-1;
            }
        }
    </style>
    
    <!-- Structured Data (JSON-LD) -->
    <script type="application/ld+json">
    {
        "@context": "https://schema.org",
        "@type": "SoftwareApplication",
        "name": "UrKnows",
        "applicationCategory": "DeveloperApplication",
        "operatingSystem": "Windows, macOS, Linux",
        "description": "AI 驱动的智能代码文档生成工具，支持自动生成代码文档、技术文档、项目文档，支持 Wiki 格式和 Markdown 格式输出。",
        "offers": {
            "@type": "Offer",
            "price": "0",
            "priceCurrency": "USD"
        },
        "aggregateRating": {
            "@type": "AggregateRating",
            "ratingValue": "5",
            "ratingCount": "1"
        },
        "featureList": [
            "AI 驱动代码文档生成",
            "支持 VSCode、Cursor、Qoder 编辑器",
            "可视化配置管理",
            "任务管理系统",
            "文档预览服务",
            "Claude Skills 导出",
            "Wiki 格式文档生成",
            "Markdown 格式文档生成",
            "代码库文档化",
            "技术文档自动生成"
        ],
        "keywords": "代码文档生成,AI文档生成,代码Wiki,技术文档生成,项目文档,代码文档化,文档自动生成,代码分析工具,文档生成器,代码文档系统,开发文档,API文档生成,代码库文档,文档工具,代码注释生成,文档生成插件,Wiki生成,Markdown文档,Claude Skills,代码文档化工具,智能文档生成,代码文档管理,文档预览,代码文档系统,开发工具,编程文档"
    }
    </script>
</head>
<body class="bg-light-bg text-light-text dark:bg-dark-bg dark:text-dark-text transition-colors duration-300 min-h-screen">
    <!-- 导航栏 -->
    <header class="sticky top-0 z-50 bg-light-card/90 dark:bg-dark-card/90 backdrop-blur-sm shadow-sm">
        <div class="container mx-auto px-4 py-4 flex justify-between items-center">
            <div class="flex items-center gap-2">
                <i class="fa-solid fa-book text-primary text-2xl"></i>
                <h1 class="text-xl font-bold">UrKnows</h1>
            </div>
            
            <div class="flex items-center gap-4">
                <!-- 导航链接 -->
                <nav class="hidden md:flex gap-6">
                    <a href="#install" class="hover:text-primary transition-colors">安装指南</a>
                    <a href="#quickstart" class="hover:text-primary transition-colors">快速开始</a>
                    <a href="#features" class="hover:text-primary transition-colors">功能特性</a>
                    <a href="#comparison" class="hover:text-primary transition-colors">轻量化优势</a>
                    <a href="#examples" class="hover:text-primary transition-colors">使用示例</a>
                    <a href="#github" class="hover:text-primary transition-colors">GitHub</a>
                </nav>
                
                <!-- 主题切换按钮 -->
                <button id="theme-toggle" class="p-2 rounded-full hover:bg-gray-200 dark:hover:bg-gray-700 transition-colors">
                    <i class="fa-solid fa-sun dark:hidden text-xl"></i>
                    <i class="fa-solid fa-moon hidden dark:block text-xl"></i>
                </button>
                
                <!-- 移动端菜单按钮 -->
                <button id="mobile-menu-btn" class="md:hidden p-2 rounded-full hover:bg-gray-200 dark:hover:bg-gray-700">
                    <i class="fa-solid fa-bars text-xl"></i>
                </button>
            </div>
        </div>
        
        <!-- 移动端导航菜单 -->
        <div id="mobile-menu" class="hidden md:hidden bg-light-card dark:bg-dark-card shadow-md">
            <div class="container mx-auto px-4 py-2 flex flex-col gap-3">
                <a href="#install" class="py-2 hover:text-primary transition-colors">安装指南</a>
                <a href="#quickstart" class="py-2 hover:text-primary transition-colors">快速开始</a>
                <a href="#features" class="py-2 hover:text-primary transition-colors">功能特性</a>
                <a href="#comparison" class="py-2 hover:text-primary transition-colors">轻量化优势</a>
                <a href="#examples" class="py-2 hover:text-primary transition-colors">使用示例</a>
                <a href="#github" class="py-2 hover:text-primary transition-colors">GitHub</a>
            </div>
        </div>
    </header>

    <main class="container mx-auto px-4 py-8">
        <!-- 英雄区 -->
        <section class="py-16 text-center">
            <h2 class="text-[clamp(2rem,5vw,3.5rem)] font-bold mb-6 text-shadow">
                <span class="text-primary">UrKnows</span> - AI 驱动的智能代码文档生成工具
            </h2>
            <p class="text-lg md:text-xl max-w-3xl mx-auto mb-8 text-gray-600 dark:text-gray-300">
                自动分析代码库并生成高质量文档（Wiki 格式、Markdown 格式），支持 VSCode、Cursor、Qoder 等编辑器，零配置上手，实时监控进度，一键预览文档！专业的代码文档生成工具，助力项目文档化和技术文档管理。
            </p>
            <div class="mt-4 inline-flex items-center gap-2 bg-green-100 dark:bg-green-900/30 text-green-800 dark:text-green-300 px-4 py-2 rounded-full text-sm font-medium">
                <i class="fa-solid fa-feather-pointed"></i>
                <span>极轻量级：资源占用仅为同类工具的 1/160</span>
            </div>
            <div class="animate-pulse-slow inline-block">
                <p class="text-xl font-semibold text-primary mb-6">准备开始了吗？🚀</p>
            </div>
            <a href="#install" class="bg-primary hover:bg-primary/90 text-white px-8 py-3 rounded-lg font-medium transition-colors">
                立即开始 <i class="fa-solid fa-arrow-right ml-2"></i>
            </a>
        </section>

        <!-- 安装指南 -->
        <section id="install" class="py-12">
            <div class="max-w-4xl mx-auto">
                <h3 class="text-2xl md:text-3xl font-bold mb-8 flex items-center">
                    <i class="fa-solid fa-download text-primary mr-3"></i>
                    安装指南
                </h3>
                
                <div class="bg-light-card dark:bg-dark-card rounded-xl shadow p-6 card-hover">
                    <div class="mb-6">
                        <p class="text-gray-600 dark:text-gray-300 mb-4">UrKnows 是一个专业的代码文档生成工具和 Wiki 生成器，支持多种编辑器，你可以选择最适合你的安装方式：</p>
                    </div>
                    
                    <div class="space-y-6">
                        <!-- VSCode 安装 -->
                        <div class="border border-gray-200 dark:border-gray-700 rounded-lg p-4">
                            <h4 class="font-semibold text-lg mb-3 flex items-center">
                                <i class="fa-brands fa-vscode text-primary mr-2"></i>
                                VSCode 安装
                            </h4>
                            <ol class="space-y-2 text-sm text-gray-600 dark:text-gray-300 ml-6">
                                <li>1. 打开 VSCode（需要 1.80.0 或更高版本）</li>
                                <li>2. 按 <code class="bg-gray-200 dark:bg-gray-700 px-2 py-1 rounded">Ctrl+Shift+X</code> (Windows/Linux) 或 <code class="bg-gray-200 dark:bg-gray-700 px-2 py-1 rounded">Cmd+Shift+X</code> (macOS) 打开扩展面板</li>
                                <li>3. 搜索 <strong class="text-primary">UrKnows</strong></li>
                                <li>4. 点击 <strong>安装</strong> 按钮</li>
                                <li>5. 安装完成后，点击左侧活动栏的 <strong>📚 UrKnows</strong> 图标开始使用</li>
                            </ol>
                        </div>
                        
                        <!-- Cursor 安装 -->
                        <div class="border border-gray-200 dark:border-gray-700 rounded-lg p-4">
                            <h4 class="font-semibold text-lg mb-3 flex items-center">
                                <i class="fa-solid fa-mouse-pointer text-primary mr-2"></i>
                                Cursor 安装
                            </h4>
                            <ol class="space-y-2 text-sm text-gray-600 dark:text-gray-300 ml-6">
                                <li>1. 打开 Cursor 编辑器</li>
                                <li>2. 按 <code class="bg-gray-200 dark:bg-gray-700 px-2 py-1 rounded">Ctrl+Shift+X</code> (Windows/Linux) 或 <code class="bg-gray-200 dark:bg-gray-700 px-2 py-1 rounded">Cmd+Shift+X</code> (macOS) 打开扩展面板</li>
                                <li>3. 搜索 <strong class="text-primary">UrKnows</strong></li>
                                <li>4. 点击 <strong>安装</strong> 按钮</li>
                                <li>5. Cursor 完全兼容 VSCode 扩展，可以直接使用</li>
                            </ol>
                        </div>
                        
                        <!-- Qoder 安装 -->
                        <div class="border border-gray-200 dark:border-gray-700 rounded-lg p-4">
                            <h4 class="font-semibold text-lg mb-3 flex items-center">
                                <i class="fa-solid fa-code text-primary mr-2"></i>
                                Qoder 安装
                            </h4>
                            <ol class="space-y-2 text-sm text-gray-600 dark:text-gray-300 ml-6">
                                <li>1. 打开 Qoder 编辑器</li>
                                <li>2. 按 <code class="bg-gray-200 dark:bg-gray-700 px-2 py-1 rounded">Ctrl+Shift+X</code> (Windows/Linux) 或 <code class="bg-gray-200 dark:bg-gray-700 px-2 py-1 rounded">Cmd+Shift+X</code> (macOS) 打开扩展面板</li>
                                <li>3. 搜索 <strong class="text-primary">UrKnows</strong></li>
                                <li>4. 点击 <strong>安装</strong> 按钮</li>
                                <li>5. Qoder 基于 VSCode 架构，完全兼容</li>
                            </ol>
                        </div>
                        
                        <!-- 手动安装 -->
                        <div class="border border-gray-200 dark:border-gray-700 rounded-lg p-4">
                            <h4 class="font-semibold text-lg mb-3 flex items-center">
                                <i class="fa-solid fa-file-zipper text-primary mr-2"></i>
                                手动安装
                            </h4>
                            <ol class="space-y-2 text-sm text-gray-600 dark:text-gray-300 ml-6">
                                <li>1. 从 <a href="https://open-vsx.org/extension/urknows/urknows" target="_blank" class="text-primary hover:underline">OpenVSX</a> 或 <a href="https://github.com/2hangchen/urknows-vscode-extension/releases" target="_blank" class="text-primary hover:underline">GitHub Releases</a> 下载 <code class="bg-gray-200 dark:bg-gray-700 px-2 py-1 rounded">.vsix</code> 文件</li>
                                <li>2. 在编辑器中按 <code class="bg-gray-200 dark:bg-gray-700 px-2 py-1 rounded">Ctrl+Shift+P</code> (或 <code class="bg-gray-200 dark:bg-gray-700 px-2 py-1 rounded">Cmd+Shift+P</code>) 打开命令面板</li>
                                <li>3. 输入 <code class="bg-gray-200 dark:bg-gray-700 px-2 py-1 rounded">Extensions: Install from VSIX...</code></li>
                                <li>4. 选择下载的 <code class="bg-gray-200 dark:bg-gray-700 px-2 py-1 rounded">.vsix</code> 文件</li>
                            </ol>
                        </div>
                    </div>
                </div>
            </div>
        </section>

        <!-- 快速开始 -->
        <section id="quickstart" class="py-12">
            <div class="max-w-4xl mx-auto">
                <h3 class="text-2xl md:text-3xl font-bold mb-8 flex items-center">
                    <i class="fa-solid fa-rocket text-primary mr-3"></i>
                    快速开始
                </h3>
                
                <div class="bg-light-card dark:bg-dark-card rounded-xl shadow p-6 card-hover">
                    <div class="space-y-6">
                        <!-- 步骤 1 -->
                        <div class="flex gap-3">
                            <span class="flex-shrink-0 w-8 h-8 bg-primary/10 dark:bg-primary/20 text-primary rounded-full flex items-center justify-center font-bold">1</span>
                            <div>
                                <h4 class="font-semibold text-lg mb-2">首次配置</h4>
                                <p class="text-gray-600 dark:text-gray-300 mb-2">安装插件后，首次使用需要配置 API 参数：</p>
                                <ul class="list-disc list-inside text-sm text-gray-600 dark:text-gray-300 space-y-1 ml-4">
                                    <li>点击左侧活动栏的 <strong>📚 UrKnows</strong> 图标</li>
                                    <li>或按 <code class="bg-gray-200 dark:bg-gray-700 px-2 py-1 rounded">Ctrl+Shift+P</code> 输入 <code class="bg-gray-200 dark:bg-gray-700 px-2 py-1 rounded">urknows: 打开配置</code></li>
                                    <li>填写 API Key、Base URL、模型名称等配置信息</li>
                                    <li>点击"保存配置"按钮，配置会自动加密存储</li>
                                </ul>
                            </div>
                        </div>
                        
                        <!-- 步骤 2 -->
                        <div class="flex gap-3">
                            <span class="flex-shrink-0 w-8 h-8 bg-primary/10 dark:bg-primary/20 text-primary rounded-full flex items-center justify-center font-bold">2</span>
                            <div>
                                <h4 class="font-semibold text-lg mb-2">生成文档</h4>
                                <p class="text-gray-600 dark:text-gray-300 mb-2">配置完成后，可以开始生成文档：</p>
                                <ul class="list-disc list-inside text-sm text-gray-600 dark:text-gray-300 space-y-1 ml-4">
                                    <li>在活动栏主页点击"生成文档"卡片</li>
                                    <li>或按 <code class="bg-gray-200 dark:bg-gray-700 px-2 py-1 rounded">Ctrl+Shift+P</code> 输入 <code class="bg-gray-200 dark:bg-gray-700 px-2 py-1 rounded">UrKnows: 生成文档</code></li>
                                    <li>或在资源管理器中右键文件夹选择"生成文档"</li>
                                    <li>在"任务"视图中查看实时进度和日志</li>
                                </ul>
                            </div>
                        </div>
                        
                        <!-- 步骤 3 -->
                        <div class="flex gap-3">
                            <span class="flex-shrink-0 w-8 h-8 bg-primary/10 dark:bg-primary/20 text-primary rounded-full flex items-center justify-center font-bold">3</span>
                            <div>
                                <h4 class="font-semibold text-lg mb-2">查看文档</h4>
                                <p class="text-gray-600 dark:text-gray-300 mb-2">生成文档后，可以立即预览：</p>
                                <ul class="list-disc list-inside text-sm text-gray-600 dark:text-gray-300 space-y-1 ml-4">
                                    <li>点击活动栏主页的"查看文档"卡片</li>
                                    <li>或按 <code class="bg-gray-200 dark:bg-gray-700 px-2 py-1 rounded">Ctrl+Shift+P</code> 输入 <code class="bg-gray-200 dark:bg-gray-700 px-2 py-1 rounded">UrKnows: 查看文档</code></li>
                                    <li>浏览器会自动打开文档预览页面</li>
                                    <li>支持文档搜索和模块树浏览</li>
                                </ul>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </section>

        <!-- 功能特性 -->
        <section id="features" class="py-12">
            <div class="max-w-4xl mx-auto">
                <h3 class="text-2xl md:text-3xl font-bold mb-8 flex items-center">
                    <i class="fa-solid fa-star text-primary mr-3"></i>
                    功能特性
                </h3>
                
                <div class="grid md:grid-cols-2 gap-6">
                    <!-- 可视化配置 -->
                    <div class="bg-light-card dark:bg-dark-card rounded-xl shadow p-6 card-hover">
                        <div class="flex items-center mb-3">
                            <i class="fa-solid fa-sliders text-primary text-2xl mr-3"></i>
                            <h4 class="font-semibold text-lg">可视化配置管理</h4>
                        </div>
                        <p class="text-gray-600 dark:text-gray-300 text-sm">图形化配置界面，直观的 Webview 界面，轻松配置所有参数。API Key 使用 VSCode SecretStorage 加密存储，安全可靠。</p>
                    </div>
                    
                    <!-- 任务管理 -->
                    <div class="bg-light-card dark:bg-dark-card rounded-xl shadow p-6 card-hover">
                        <div class="flex items-center mb-3">
                            <i class="fa-solid fa-tasks text-primary text-2xl mr-3"></i>
                            <h4 class="font-semibold text-lg">任务管理系统</h4>
                        </div>
                        <p class="text-gray-600 dark:text-gray-300 text-sm">后台执行文档生成任务，实时查看任务进度、状态和日志输出。自动保存最近 50 个任务的历史记录，支持失败任务一键重试。</p>
                    </div>
                    
                    <!-- 文档预览 -->
                    <div class="bg-light-card dark:bg-dark-card rounded-xl shadow p-6 card-hover">
                        <div class="flex items-center mb-3">
                            <i class="fa-solid fa-eye text-primary text-2xl mr-3"></i>
                            <h4 class="font-semibold text-lg">文档预览服务</h4>
                        </div>
                        <p class="text-gray-600 dark:text-gray-300 text-sm">内置 HTTP 服务器，自动启动本地预览。智能选择可用端口（8080-8090），提供 metadata 和 module-tree API，支持文档内容搜索。</p>
                    </div>
                    
                    <!-- Claude Skills -->
                    <div class="bg-light-card dark:bg-dark-card rounded-xl shadow p-6 card-hover">
                        <div class="flex items-center mb-3">
                            <i class="fa-solid fa-robot text-primary text-2xl mr-3"></i>
                            <h4 class="font-semibold text-lg">Claude Skills 导出</h4>
                        </div>
                        <p class="text-gray-600 dark:text-gray-300 text-sm">将生成的文档转换为 Claude Skills 规范格式。使用 LLM 自动优化 Skill 名称和描述，生成完整的 SKILL.md、OVERVIEW.md、MODULES.md 等文件结构。</p>
                    </div>
                </div>
            </div>
        </section>

        <!-- 轻量化优势 -->
        <section id="comparison" class="py-12 bg-gray-50 dark:bg-gray-900/50">
            <div class="max-w-4xl mx-auto">
                <h3 class="text-2xl md:text-3xl font-bold mb-8 flex items-center">
                    <i class="fa-solid fa-feather-pointed text-primary mr-3"></i>
                    轻量化优势
                </h3>
                
                <div class="bg-light-card dark:bg-dark-card rounded-xl shadow p-6 card-hover">
                    <p class="text-gray-600 dark:text-gray-300 mb-6">
                        相比传统的代码文档生成工具，UrKnows 插件在保持相同文档生成质量的同时，具有显著的轻量化优势：
                    </p>
                    
                    <div class="grid md:grid-cols-2 gap-6">
                        <div class="flex items-start gap-4">
                            <div class="flex-shrink-0 w-12 h-12 bg-primary/10 dark:bg-primary/20 rounded-lg flex items-center justify-center">
                                <i class="fa-solid fa-feather-pointed text-primary text-xl"></i>
                            </div>
                            <div>
                                <h4 class="font-semibold text-lg mb-2">极低资源占用</h4>
                                <p class="text-gray-600 dark:text-gray-300 text-sm">内存和存储占用远低于传统方案，适合资源受限环境</p>
                            </div>
                        </div>
                        
                        <div class="flex items-start gap-4">
                            <div class="flex-shrink-0 w-12 h-12 bg-primary/10 dark:bg-primary/20 rounded-lg flex items-center justify-center">
                                <i class="fa-solid fa-bolt text-primary text-xl"></i>
                            </div>
                            <div>
                                <h4 class="font-semibold text-lg mb-2">即装即用</h4>
                                <p class="text-gray-600 dark:text-gray-300 text-sm">无需复杂部署，一键安装即可使用，启动速度快</p>
                            </div>
                        </div>
                        
                        <div class="flex items-start gap-4">
                            <div class="flex-shrink-0 w-12 h-12 bg-primary/10 dark:bg-primary/20 rounded-lg flex items-center justify-center">
                                <i class="fa-solid fa-sliders text-primary text-xl"></i>
                            </div>
                            <div>
                                <h4 class="font-semibold text-lg mb-2">零配置上手</h4>
                                <p class="text-gray-600 dark:text-gray-300 text-sm">可视化界面，无需记忆命令行参数，降低使用门槛</p>
                            </div>
                        </div>
                        
                        <div class="flex items-start gap-4">
                            <div class="flex-shrink-0 w-12 h-12 bg-primary/10 dark:bg-primary/20 rounded-lg flex items-center justify-center">
                                <i class="fa-solid fa-plug text-primary text-xl"></i>
                            </div>
                            <div>
                                <h4 class="font-semibold text-lg mb-2">深度集成</h4>
                                <p class="text-gray-600 dark:text-gray-300 text-sm">直接在编辑器中使用，无需切换工具，提升开发效率</p>
                            </div>
                        </div>
                    </div>
                    
                    <div class="mt-6 p-4 bg-blue-50 dark:bg-blue-900/20 rounded-lg border-l-4 border-primary">
                        <p class="text-gray-700 dark:text-gray-300">
                            <strong>结论：</strong>UrKnows 插件更适合个人开发者和资源受限环境，提供了轻量、便捷的代码文档生成解决方案。
                        </p>
                    </div>
                </div>
            </div>
        </section>

        <!-- 使用示例 -->
        <section id="examples" class="py-12">
            <div class="max-w-4xl mx-auto">
                <h3 class="text-2xl md:text-3xl font-bold mb-8 flex items-center">
                    <i class="fa-solid fa-code text-primary mr-3"></i>
                    使用示例
                </h3>
                
                <div class="bg-light-card dark:bg-dark-card rounded-xl shadow p-6 card-hover">
                    <div class="mb-6">
                        <p class="text-gray-600 dark:text-gray-300">以下是几个常用场景的使用示例，帮助你快速上手代码文档生成和 Wiki 文档创建：</p>
                    </div>
                    
                    <div class="space-y-6">
                        <!-- 示例 1 -->
                        <div>
                            <h4 class="font-semibold text-lg mb-2">配置 API 参数</h4>
                            <div class="bg-gray-100 dark:bg-gray-800 rounded-lg p-4 font-mono text-sm overflow-x-auto">
                                <pre>1. 打开配置界面
   - 点击活动栏 📚 UrKnows 图标
   - 或使用命令: urknows: 打开配置

2. 填写配置信息
   - API Key: 您的 LLM API 密钥
   - Base URL: https://api.anthropic.com
   - 模型名称: claude-sonnet-4
   - 输出目录: ./docs

3. 保存配置
   - 点击"保存配置"按钮
   - 配置会自动加密存储</pre>
                            </div>
                        </div>
                        
                        <!-- 示例 2 -->
                        <div>
                            <h4 class="font-semibold text-lg mb-2">生成项目文档</h4>
                            <div class="bg-gray-100 dark:bg-gray-800 rounded-lg p-4 font-mono text-sm overflow-x-auto">
                                <pre>1. 选择生成方式
   - 在主页点击"生成文档"卡片
   - 或使用命令: UrKnows: 生成文档
   - 或右键文件夹选择"生成文档"

2. 监控任务进度
   - 在"任务"视图中查看实时进度
   - 查看日志了解详细执行信息
   - 查看统计信息（文件数、模块数、Token 使用量）

3. 查看生成结果
   - 生成完成后显示输出目录
   - 点击"查看文档"预览生成的文档</pre>
                            </div>
                        </div>
                        
                        <!-- 示例 3 -->
                        <div>
                            <h4 class="font-semibold text-lg mb-2">导出为 Claude Skills</h4>
                            <div class="bg-gray-100 dark:bg-gray-800 rounded-lg p-4 font-mono text-sm overflow-x-auto">
                                <pre>1. 确保已生成文档
   - 文档生成完成后才能导出

2. 执行导出命令
   - 按 Ctrl+Shift+P 输入: urknows: 导出为 Claude Skills
   - 选择导出位置（项目目录或个人目录）

3. 查看导出结果
   - 转换后的文件包含完整的 Claude Skills 规范结构
   - SKILL.md - 技能描述
   - OVERVIEW.md - 项目概览
   - MODULES.md - 模块列表</pre>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </section>

        <!-- GitHub 地址 -->
        <section id="github" class="py-12">
            <div class="max-w-4xl mx-auto">
                <h3 class="text-2xl md:text-3xl font-bold mb-8 flex items-center">
                    <i class="fa-brands fa-github text-primary mr-3"></i>
                    GitHub 资源
                </h3>
                
                <div class="bg-light-card dark:bg-dark-card rounded-xl shadow p-6 card-hover text-center">
                    <p class="text-gray-600 dark:text-gray-300 mb-6">获取更多插件信息、使用教程、Wiki 文档生成指南和最新更新，请访问以下资源：</p>
                    
                    <a href="https://open-vsx.org/extension/urknows/urknows-vscode-extension" target="_blank" class="inline-flex items-center justify-center bg-gray-800 hover:bg-gray-700 text-white px-6 py-3 rounded-lg transition-colors mb-4">
                        <i class="fa-solid fa-puzzle-piece mr-2"></i>
                        OpenVSX 扩展市场
                    </a>
                    
                    <div class="flex flex-wrap justify-center gap-4">
                        <a href="https://github.com/2hangchen/urknows-vscode-extension" target="_blank" class="text-primary hover:underline flex items-center">
                            <i class="fa-brands fa-github mr-1"></i> GitHub 仓库
                        </a>
                        <a href="https://github.com/2hangchen/urknows-vscode-extension/issues" target="_blank" class="text-primary hover:underline flex items-center">
                            <i class="fa-solid fa-bug mr-1"></i> 问题反馈
                        </a>
                        <a href="https://github.com/2hangchen/urknows-vscode-extension/discussions" target="_blank" class="text-primary hover:underline flex items-center">
                            <i class="fa-solid fa-comments mr-1"></i> 讨论区
                        </a>
                    </div>
                </div>
            </div>
        </section>

        <!-- 行动召唤区 -->
        <section class="py-16 text-center">
            <div class="max-w-3xl mx-auto bg-primary/10 dark:bg-primary/20 rounded-2xl p-8">
                <h3 class="text-2xl md:text-3xl font-bold mb-4">准备开始了吗？</h3>
                <p class="text-gray-600 dark:text-gray-300 mb-6">现在就安装 UrKnows 插件，开启你的智能代码文档生成和 Wiki 文档创建之旅！让 AI 帮你自动生成高质量的技术文档、项目文档和代码文档。</p>
                <div class="flex flex-wrap justify-center gap-4">
                    <a href="https://open-vsx.org/extension/urknows/urknows-vscode-extension" target="_blank" class="bg-primary hover:bg-primary/90 text-white px-6 py-3 rounded-lg font-medium transition-colors">
                        <i class="fa-solid fa-download mr-2"></i> 安装 UrKnows 插件
                    </a>
                    <a href="https://github.com/2hangchen/urknows-vscode-extension" target="_blank" class="bg-gray-800 hover:bg-gray-700 text-white px-6 py-3 rounded-lg font-medium transition-colors">
                        <i class="fa-brands fa-github mr-2"></i> 查看 GitHub
                    </a>
                </div>
            </div>
        </section>
    </main>

    <!-- 页脚 -->
    <footer class="bg-light-card dark:bg-dark-card border-t border-gray-200 dark:border-gray-700 py-8">
        <div class="container mx-auto px-4 text-center">
            <div class="mb-4">
                <i class="fa-solid fa-book text-primary text-2xl mb-2"></i>
                <p class="font-semibold">UrKnows 插件使用指南</p>
            </div>
            <p class="text-sm text-gray-600 dark:text-gray-300">
                © 2025 UrKnows | AI 驱动的智能代码文档生成工具
            </p>
        </div>
    </footer>

    <!-- JavaScript -->
    <script>
        // 主题切换功能
        const themeToggle = document.getElementById('theme-toggle');
        const htmlElement = document.documentElement;
        
        // 初始化主题
        if (localStorage.getItem('theme') === 'dark' || 
            (!localStorage.getItem('theme') && window.matchMedia('(prefers-color-scheme: dark)').matches)) {
            htmlElement.classList.add('dark');
        } else {
            htmlElement.classList.remove('dark');
        }
        
        // 切换主题
        themeToggle.addEventListener('click', () => {
            htmlElement.classList.toggle('dark');
            if (htmlElement.classList.contains('dark')) {
                localStorage.setItem('theme', 'dark');
            } else {
                localStorage.setItem('theme', 'light');
            }
        });
        
        // 移动端菜单切换
        const mobileMenuBtn = document.getElementById('mobile-menu-btn');
        const mobileMenu = document.getElementById('mobile-menu');
        
        mobileMenuBtn.addEventListener('click', () => {
            mobileMenu.classList.toggle('hidden');
        });
        
        // 平滑滚动
        document.querySelectorAll('a[href^="#"]').forEach(anchor => {
            anchor.addEventListener('click', function (e) {
                e.preventDefault();
                
                // 关闭移动端菜单
                mobileMenu.classList.add('hidden');
                
                const targetId = this.getAttribute('href');
                const targetElement = document.querySelector(targetId);
                
                if (targetElement) {
                    window.scrollTo({
                        top: targetElement.offsetTop - 80,
                        behavior: 'smooth'
                    });
                }
            });
        });
        
        // 滚动时导航栏样式变化
        window.addEventListener('scroll', () => {
            const header = document.querySelector('header');
            if (window.scrollY > 50) {
                header.classList.add('shadow');
            } else {
                header.classList.remove('shadow');
            }
        });
    </script>
</body>
</html>
