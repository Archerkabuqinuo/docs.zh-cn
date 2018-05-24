---
title: -deterministic（C# 编译器选项）
ms.date: 04/12/2018
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /deterministic
helpviewer_keywords:
- -deterministic compiler option [C#]
- deterministic compiler option [C#]
- /deterministic compiler option [C#]
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f6dd597f726b5bbc40feb4cc6f5b03acabd92f4a
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/27/2018
---
# <a name="-deterministic"></a><span data-ttu-id="d7d45-102">-deterministic</span><span class="sxs-lookup"><span data-stu-id="d7d45-102">-deterministic</span></span>

<span data-ttu-id="d7d45-103">如果输入相同，则会导致编译器生成的程序集其逐字节输出在整个编译期间中相同。</span><span class="sxs-lookup"><span data-stu-id="d7d45-103">Causes the compiler to produce an assembly whose byte-for-byte output is identical across compilations for identical inputs.</span></span> 

## <a name="syntax"></a><span data-ttu-id="d7d45-104">语法</span><span class="sxs-lookup"><span data-stu-id="d7d45-104">Syntax</span></span>

```
-deterministic
```

## <a name="remarks"></a><span data-ttu-id="d7d45-105">备注</span><span class="sxs-lookup"><span data-stu-id="d7d45-105">Remarks</span></span>

<span data-ttu-id="d7d45-106">默认情况下，一组给定输入的编译器输出是唯一的，因为编译器会添加时间戳和随意数字生成的 GUID。</span><span class="sxs-lookup"><span data-stu-id="d7d45-106">By default, compiler output from a given set of inputs is unique, since the compiler adds a timestamp and a GUID that is generated from random numbers.</span></span> <span data-ttu-id="d7d45-107">使用 `-deterministic` 选项生成确定性的程序集，只要输入保持不变，该程序集的二进制内容在整个编译中都是相同的。</span><span class="sxs-lookup"><span data-stu-id="d7d45-107">You use the `-deterministic` option to produce a *deterministic assembly*, one whose binary content is identical across compilations as long as the input remains the same.</span></span>

<span data-ttu-id="d7d45-108">出于确定性目的，编译器会考虑以下输入：</span><span class="sxs-lookup"><span data-stu-id="d7d45-108">The compiler considers the following inputs for the purpose of determinism:</span></span>

- <span data-ttu-id="d7d45-109">命令行参数序列。</span><span class="sxs-lookup"><span data-stu-id="d7d45-109">The sequence of command-line parameters.</span></span>
- <span data-ttu-id="d7d45-110">编译器 .rsp 响应文件的内容。</span><span class="sxs-lookup"><span data-stu-id="d7d45-110">The contents of the compiler's .rsp response file.</span></span>
- <span data-ttu-id="d7d45-111">所用编译器的精确版本及其引用的程序集。</span><span class="sxs-lookup"><span data-stu-id="d7d45-111">The precise version of the compiler used, and its referenced assemblies.</span></span>
- <span data-ttu-id="d7d45-112">当前目录路径。</span><span class="sxs-lookup"><span data-stu-id="d7d45-112">The current directory path.</span></span>
- <span data-ttu-id="d7d45-113">直接或间接地显式传递到编译器的所有文件的二进制内容，包括：</span><span class="sxs-lookup"><span data-stu-id="d7d45-113">The binary contents of all files explicitly passed to the compiler either directly or indirectly, including:</span></span>
    - <span data-ttu-id="d7d45-114">源文件</span><span class="sxs-lookup"><span data-stu-id="d7d45-114">Source files</span></span>
    - <span data-ttu-id="d7d45-115">引用的程序集</span><span class="sxs-lookup"><span data-stu-id="d7d45-115">Referenced assemblies</span></span>
    - <span data-ttu-id="d7d45-116">引用的模块</span><span class="sxs-lookup"><span data-stu-id="d7d45-116">Referenced modules</span></span>
    - <span data-ttu-id="d7d45-117">资源</span><span class="sxs-lookup"><span data-stu-id="d7d45-117">Resources</span></span>
    - <span data-ttu-id="d7d45-118">强名称密钥文件</span><span class="sxs-lookup"><span data-stu-id="d7d45-118">The strong name key file</span></span>
    - <span data-ttu-id="d7d45-119">@ 响应文件</span><span class="sxs-lookup"><span data-stu-id="d7d45-119">@ response files</span></span>
    - <span data-ttu-id="d7d45-120">分析器</span><span class="sxs-lookup"><span data-stu-id="d7d45-120">Analyzers</span></span>
    - <span data-ttu-id="d7d45-121">规则集</span><span class="sxs-lookup"><span data-stu-id="d7d45-121">Rulesets</span></span>
    - <span data-ttu-id="d7d45-122">分析器可能使用的其他文件</span><span class="sxs-lookup"><span data-stu-id="d7d45-122">Additional files that may be used by analyzers</span></span>
- <span data-ttu-id="d7d45-123">当前区域性（针对生成诊断和异常消息的语言）。</span><span class="sxs-lookup"><span data-stu-id="d7d45-123">The current culture (for the language in which diagnostics and exception messages are produced).</span></span>
- <span data-ttu-id="d7d45-124">在未指定编码情况下使用的默认编码（或当前代码页）。</span><span class="sxs-lookup"><span data-stu-id="d7d45-124">The default encoding (or the current code page) if the encoding is not specified.</span></span>
- <span data-ttu-id="d7d45-125">编译器搜索路径（例如，由`/lib` 或 `/recurse` 指定）上文件是否存在及其内容。</span><span class="sxs-lookup"><span data-stu-id="d7d45-125">The existence, non-existence, and contents of files on the compiler's search paths (specified, for example, by `/lib` or `/recurse`).</span></span>
- <span data-ttu-id="d7d45-126">运行编译器的 CLR 平台。</span><span class="sxs-lookup"><span data-stu-id="d7d45-126">The CLR platform on which the compiler is run.</span></span>
- <span data-ttu-id="d7d45-127">`%LIBPATH%` 的值，该值会影响分析器的依赖项加载。</span><span class="sxs-lookup"><span data-stu-id="d7d45-127">The value of `%LIBPATH%`, which can affect analyzer dependency loading.</span></span>

<span data-ttu-id="d7d45-128">当源公开可用时，可使用确定性编译来确定是否从可信源编译二进制内容。</span><span class="sxs-lookup"><span data-stu-id="d7d45-128">When sources are publicly available, deterministic compilation can be used for establishing whether a binary is compiled from a trusted source.</span></span> <span data-ttu-id="d7d45-129">它还可有效用于连续生成系统，确定是否需要执行依赖于二进制内容更改的生成步骤。</span><span class="sxs-lookup"><span data-stu-id="d7d45-129">It can also be useful in a continuous build system for determining whether build steps that are dependent on changes to a binary need to be executed.</span></span> 

## <a name="see-also"></a><span data-ttu-id="d7d45-130">请参阅</span><span class="sxs-lookup"><span data-stu-id="d7d45-130">See Also</span></span>  
 [<span data-ttu-id="d7d45-131">C# 编译器选项</span><span class="sxs-lookup"><span data-stu-id="d7d45-131">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
 [<span data-ttu-id="d7d45-132">管理项目和解决方案属性</span><span class="sxs-lookup"><span data-stu-id="d7d45-132">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)