---
title: "快速入門 - 集合 - C# 指南"
description: "透過在此快速入門中探索 List 集合來了解 C#。"
keywords: "C#, Get Started, tutorial, collections, List, 快速入門, 教學課程, 集合, 清單"
author: billwagner
ms.author: wiwagn
ms.date: 10/13/2017
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.openlocfilehash: 51b190fba32186cb4c52ccd773274d9ae22c8efb
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="c-quick-start-collections"></a><span data-ttu-id="4928d-104">C# 快速入門：集合</span><span class="sxs-lookup"><span data-stu-id="4928d-104">C# Quick start: Collections</span></span> #

<span data-ttu-id="4928d-105">本教學課程提供 C# 語言的簡介，以及 <xref:System.Collections.Generic.List%601> 類別的基礎知識。</span><span class="sxs-lookup"><span data-stu-id="4928d-105">This tutorial provides an introduction to the C# language and the basics of the <xref:System.Collections.Generic.List%601> class.</span></span>

## <a name="a-simple-list-example"></a><span data-ttu-id="4928d-106">簡單的清單範例。</span><span class="sxs-lookup"><span data-stu-id="4928d-106">A simple list example.</span></span>

> [!NOTE]
> <span data-ttu-id="4928d-107">如果您是從您於 [dot.net](https://dot.net/) \(英文\) 中撰寫的程式碼開始，您已經具有要在本節中撰寫的程式碼。</span><span class="sxs-lookup"><span data-stu-id="4928d-107">If you're starting from the code you wrote in [dot.net](https://dot.net/), you already have the code written in this section.</span></span> <span data-ttu-id="4928d-108">請跳至[修改清單內容](#modify-list-contents)。</span><span class="sxs-lookup"><span data-stu-id="4928d-108">Jump to [Modify list contents](#modify-list-contents).</span></span>

<span data-ttu-id="4928d-109">本課程假設您已經完成線上快速入門，並已安裝 [.NET Core SDK](http://dot.net/core) \(英文\) 和 [Visual Studio Code](https://code.visualstudio.com/) \(英文\)。</span><span class="sxs-lookup"><span data-stu-id="4928d-109">This lesson assumes you've finished the online quick starts, and you've installed the [.NET Core SDK](http://dot.net/core) and [Visual Studio Code](https://code.visualstudio.com/).</span></span> 

<span data-ttu-id="4928d-110">建立名為 **list-quickstart** 的目錄。</span><span class="sxs-lookup"><span data-stu-id="4928d-110">Create a directory named **list-quickstart**.</span></span> <span data-ttu-id="4928d-111">將該目錄設為目前的目錄，並執行 `dotnet new console`。</span><span class="sxs-lookup"><span data-stu-id="4928d-111">Make that the current directory and run `dotnet new console`.</span></span>

<span data-ttu-id="4928d-112">在您最愛的編輯器中開啟 **Program.cs**，並以下列內容取代現有的程式碼：</span><span class="sxs-lookup"><span data-stu-id="4928d-112">Open **Program.cs** in your favorite editor, and replace the existing code with the following:</span></span>

```csharp
using System;
using System.Collections.Generic;

namespace list_quickstart
{
    class Program
    {
        static void Main(string[] args)
        {
            var names = new List<string> { "<name>", "Ana", "Felipe" };
            foreach (var name in names)
            {
                Console.WriteLine($"Hello {name.ToUpper()}!");
            }
        }
    }
}
```

<span data-ttu-id="4928d-113">以您的名稱取代 `<name>`。</span><span class="sxs-lookup"><span data-stu-id="4928d-113">Replace `<name>` with your name.</span></span> <span data-ttu-id="4928d-114">儲存 **Program.cs**。</span><span class="sxs-lookup"><span data-stu-id="4928d-114">Save **Program.cs**.</span></span> <span data-ttu-id="4928d-115">在主控台視窗中輸入 `dotnet run` 來嘗試它。</span><span class="sxs-lookup"><span data-stu-id="4928d-115">Type `dotnet run` in your console window to try it.</span></span>

<span data-ttu-id="4928d-116">您剛才已建立字串清單，在該清單中新增三個名稱，並以全部大寫的形式列印出那些名稱。</span><span class="sxs-lookup"><span data-stu-id="4928d-116">You've just created a list of strings, added three names to that list, and printed out the names in all CAPS.</span></span> <span data-ttu-id="4928d-117">您會使用從先前的快速入門中學習到的概念，來在清單中執行迴圈。</span><span class="sxs-lookup"><span data-stu-id="4928d-117">You're using concepts that you've learned in earlier quick starts to loop through the list.</span></span>

<span data-ttu-id="4928d-118">顯示名稱的程式碼會運用**字串插值**。</span><span class="sxs-lookup"><span data-stu-id="4928d-118">The code to display names makes use of **interpolated strings**.</span></span>  <span data-ttu-id="4928d-119">當您在 `string` 的前方放置 `$` 時，您可以在字串宣告中內嵌 C# 程式碼。</span><span class="sxs-lookup"><span data-stu-id="4928d-119">When you precede a `string` with the `$` character, you can embed C# code in the string declaration.</span></span> <span data-ttu-id="4928d-120">實際的字串會以它所產生的值取代 C# 程式碼。</span><span class="sxs-lookup"><span data-stu-id="4928d-120">The actual string replaces that C# code with the value it generates.</span></span> <span data-ttu-id="4928d-121">在此範例中，它會以每個 (轉換成大寫字母的) 名稱取代 `{name.ToUpper()}`，因為您呼叫了 <xref:System.String.ToUpper%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="4928d-121">In this example, it replaces the `{name.ToUpper()}` with each name, converted to capital letters, because you called the <xref:System.String.ToUpper%2A> method.</span></span>

<span data-ttu-id="4928d-122">讓我們繼續探索。</span><span class="sxs-lookup"><span data-stu-id="4928d-122">Let's keep exploring.</span></span>
    
## <a name="modify-list-contents"></a><span data-ttu-id="4928d-123">修改清單內容</span><span class="sxs-lookup"><span data-stu-id="4928d-123">Modify list contents</span></span>

<span data-ttu-id="4928d-124">您所建立的集合會使用 <xref:System.Collections.Generic.List%601> 類型。</span><span class="sxs-lookup"><span data-stu-id="4928d-124">The collection you created uses the <xref:System.Collections.Generic.List%601> type.</span></span> <span data-ttu-id="4928d-125">此類型會儲存元素的序列。</span><span class="sxs-lookup"><span data-stu-id="4928d-125">This type stores sequences of elements.</span></span> <span data-ttu-id="4928d-126">您會在角括弧之間指定元素的類型。</span><span class="sxs-lookup"><span data-stu-id="4928d-126">You specify the type of the elements between the angle brackets.</span></span>
    
<span data-ttu-id="4928d-127">此 <xref:System.Collections.Generic.List%601> 類型的其中一個重要層面，在於它可以擴張或縮小，使您可以新增或移除元素。</span><span class="sxs-lookup"><span data-stu-id="4928d-127">One important aspect of this <xref:System.Collections.Generic.List%601> type is that it can grow or shrink, enabling you to add or remove elements.</span></span> <span data-ttu-id="4928d-128">在 `Main` 方法中關閉 `}` 之前，新增下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="4928d-128">Add this code before the closing `}` in the `Main` method:</span></span>

```csharp
Console.WriteLine();
names.Add("Maria");
names.Add("Bill");
names.Remove("Ana");
foreach (var name in names)
{
    Console.WriteLine($"Hello {name.ToUpper()}!");
}
```

<span data-ttu-id="4928d-129">您已在清單末端新增兩個額外的名稱。</span><span class="sxs-lookup"><span data-stu-id="4928d-129">You've added two more names to the end of the list.</span></span> <span data-ttu-id="4928d-130">您也移除了一個名稱。</span><span class="sxs-lookup"><span data-stu-id="4928d-130">You've also removed one as well.</span></span> <span data-ttu-id="4928d-131">儲存檔案，並輸入 `dotnet run` 來嘗試它。</span><span class="sxs-lookup"><span data-stu-id="4928d-131">Save the file, and type `dotnet run` to try it.</span></span>
    
<span data-ttu-id="4928d-132"><xref:System.Collections.Generic.List%601> 也可讓您透過**索引**參考個別的項目。</span><span class="sxs-lookup"><span data-stu-id="4928d-132">The <xref:System.Collections.Generic.List%601> enables you to reference individual items by **index** as well.</span></span> <span data-ttu-id="4928d-133">您需將索引放在 `[` 和 `]` 語彙基元之間，位於清單名稱之後。</span><span class="sxs-lookup"><span data-stu-id="4928d-133">You place the index between `[` and `]` tokens following the list name.</span></span> <span data-ttu-id="4928d-134">C# 使用 0 作為第一個索引。</span><span class="sxs-lookup"><span data-stu-id="4928d-134">C# uses 0 for the first index.</span></span> <span data-ttu-id="4928d-135">將下列程式碼新增至您剛才新增的程式碼下方，然後嘗試它：</span><span class="sxs-lookup"><span data-stu-id="4928d-135">Add this code directly below the code you just added and try it:</span></span>

```csharp
Console.WriteLine($"My name is {names[0]}");
Console.WriteLine($"I've added {names[2]} and {names[3]} to the list");
```

<span data-ttu-id="4928d-136">您無法存取位於清單結尾之外的索引。</span><span class="sxs-lookup"><span data-stu-id="4928d-136">You cannot access an index beyond the end of the list.</span></span> <span data-ttu-id="4928d-137">請記住，索引是從 0 開始，因此最大的有效索引數目為清單項目數目減去 1。</span><span class="sxs-lookup"><span data-stu-id="4928d-137">Remember that indices start at 0, so the largest valid index is one less than the number of items in the list.</span></span> <span data-ttu-id="4928d-138">您可以使用 <xref:System.Collections.Generic.List%601.Count%2A> 屬性檢查清單的長度。</span><span class="sxs-lookup"><span data-stu-id="4928d-138">You can check how long the list is using the <xref:System.Collections.Generic.List%601.Count%2A> property.</span></span> <span data-ttu-id="4928d-139">在 Main 方法的結尾，加入下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="4928d-139">Add the following code at the end of the Main method:</span></span>

```csharp
Console.WriteLine($"The list has {names.Count} people in it");
 ```

<span data-ttu-id="4928d-140">儲存檔案，然後再次輸入 `dotnet run` 以查看結果。</span><span class="sxs-lookup"><span data-stu-id="4928d-140">Save the file, and type `dotnet run` again to see the results.</span></span>    

## <a name="search-and-sort-lists"></a><span data-ttu-id="4928d-141">針對清單進行搜尋和排序</span><span class="sxs-lookup"><span data-stu-id="4928d-141">Search and sort lists</span></span>
<span data-ttu-id="4928d-142">我們的範例所使用的清單相對較小，但是您的應用程式可能經常會建立具有更多元素的清單，數量甚至會達數千個之多。</span><span class="sxs-lookup"><span data-stu-id="4928d-142">Our samples use relatively small lists, but your applications may often create lists with many more elements, sometimes numbering in the thousands.</span></span> <span data-ttu-id="4928d-143">若要在這些較大的集合中尋找元素，您需要在清單中搜尋不同的項目。</span><span class="sxs-lookup"><span data-stu-id="4928d-143">To find elements in these larger collections, you need to search the list for different items.</span></span> <span data-ttu-id="4928d-144"><xref:System.Collections.Generic.List%601.IndexOf%2A> 方法會搜尋項目，並傳回該項目的索引。</span><span class="sxs-lookup"><span data-stu-id="4928d-144">The <xref:System.Collections.Generic.List%601.IndexOf%2A> method searches for an item and returns the index of the item.</span></span> <span data-ttu-id="4928d-145">將下列程式碼新增到 `Main` 方法的底部：</span><span class="sxs-lookup"><span data-stu-id="4928d-145">Add this code to the bottom of your `Main` method:</span></span>

```csharp
var index = names.IndexOf("Felipe");
if (index == -1)
{
    Console.WriteLine($"When an item is not found, IndexOf returns {index}");
} else
{
    Console.WriteLine($"The name {names[index]} is at index {index}");
}

index = names.IndexOf("Not Found");
if (index == -1)
{
    Console.WriteLine($"When an item is not found, IndexOf returns {index}");
} else
{
    Console.WriteLine($"The name {names[index]} is at index {index}");
    
}
```

<span data-ttu-id="4928d-146">也可以對您清單中的項目進行排序。</span><span class="sxs-lookup"><span data-stu-id="4928d-146">The items in your list can be sorted as well.</span></span> <span data-ttu-id="4928d-147"><xref:System.Collections.Generic.List%601.Sort%2A> 方法會依項目的一般順序方式，對清單中的所有項目進行排序 (針對字串會依字母順序排列)。</span><span class="sxs-lookup"><span data-stu-id="4928d-147">The <xref:System.Collections.Generic.List%601.Sort%2A> method sorts all the items in the list in their normal order (alphabetically in the case of strings).</span></span> <span data-ttu-id="4928d-148">將下列程式碼新增到 `Main` 方法的底部：</span><span class="sxs-lookup"><span data-stu-id="4928d-148">Add this code to the bottom of our `Main` method:</span></span>

```csharp
names.Sort();
foreach (var name in names)
{
    Console.WriteLine($"Hello {name.ToUpper()}!");
}
```

<span data-ttu-id="4928d-149">儲存檔案並輸入 `dotnet run` 以嘗試此最新版本。</span><span class="sxs-lookup"><span data-stu-id="4928d-149">Save the file and type `dotnet run` to try this latest version.</span></span>

<span data-ttu-id="4928d-150">在開始下一節之前，讓我們將目前的程式碼移到另一個個別的方法。</span><span class="sxs-lookup"><span data-stu-id="4928d-150">Before you start the next section, let's move the current code into a separate method.</span></span> <span data-ttu-id="4928d-151">這可讓您更輕鬆地開始處理新的範例。</span><span class="sxs-lookup"><span data-stu-id="4928d-151">That makes it easier to start working with a new example.</span></span> <span data-ttu-id="4928d-152">將 `Main` 方法重新命名為 `WorkingWithStrings`，然後撰寫會呼叫 `WorkingWithStrings` 的新 `Main` 方法。</span><span class="sxs-lookup"><span data-stu-id="4928d-152">Rename your `Main` method to `WorkingWithStrings` and write a new `Main` method that calls `WorkingWithStrings`.</span></span> <span data-ttu-id="4928d-153">當您完成時，您的程式碼看起來應該像這樣：</span><span class="sxs-lookup"><span data-stu-id="4928d-153">When you have finished, your code should look like this:</span></span>

```csharp
using System;
using System.Collections.Generic;

namespace list_quickstart
{
    class Program
    {
        static void Main(string[] args)
        {
            WorkingWithStrings();
        }

        public static void WorkingWithStrings()
        {
            var names = new List<string> { "<name>", "Ana", "Felipe" };
            foreach (var name in names)
            {
                Console.WriteLine($"Hello {name.ToUpper()}!");
            }

            Console.WriteLine();
            names.Add("Maria");
            names.Add("Bill");
            names.Remove("Ana");
            foreach (var name in names)
            {
                Console.WriteLine($"Hello {name.ToUpper()}!");
            }

            Console.WriteLine($"My name is {names[0]}");
            Console.WriteLine($"I've added {names[2]} and {names[3]} to the list");

            Console.WriteLine($"The list has {names.Count} people in it");

            var index = names.IndexOf("Felipe");
            Console.WriteLine($"The name {names[index]} is at index {index}");

            var notFound = names.IndexOf("Not Found");
            Console.WriteLine($"When an item is not found, IndexOf returns {notFound}");

            names.Sort();
            foreach (var name in names)
            {
                Console.WriteLine($"Hello {name.ToUpper()}!");
            }
        }
    }
}
```

## <a name="lists-of-other-types"></a><span data-ttu-id="4928d-154">其他類型的清單</span><span class="sxs-lookup"><span data-stu-id="4928d-154">Lists of other types</span></span>

<span data-ttu-id="4928d-155">到目前為止，您都是使用清單中的 `string` 類型。</span><span class="sxs-lookup"><span data-stu-id="4928d-155">You've been using the `string` type in lists so far.</span></span> <span data-ttu-id="4928d-156">讓我們使用不同的類型建立 <xref:System.Collections.Generic.List%601>。</span><span class="sxs-lookup"><span data-stu-id="4928d-156">Let's make a <xref:System.Collections.Generic.List%601> using a different type.</span></span> <span data-ttu-id="4928d-157">讓我們來建置一組數字。</span><span class="sxs-lookup"><span data-stu-id="4928d-157">Let's build a set of numbers.</span></span> 

<span data-ttu-id="4928d-158">將下列內容新增到新 `Main` 方法的底部：</span><span class="sxs-lookup"><span data-stu-id="4928d-158">Add the following to the bottom of your new `Main` method:</span></span>

```csharp
var fibonacciNumbers = new List<int> {1, 1};
```

<span data-ttu-id="4928d-159">這將會建立整數清單，並將前兩個整數設定為 1 的值。</span><span class="sxs-lookup"><span data-stu-id="4928d-159">That creates a list of integers, and sets the first two integers to the value 1.</span></span> <span data-ttu-id="4928d-160">這是*費氏數列*的前兩個值。</span><span class="sxs-lookup"><span data-stu-id="4928d-160">These are the first two values of a *Fibonacci Sequence*, a sequence of numbers.</span></span> <span data-ttu-id="4928d-161">這兩個值之後每個費式數列數字，都會是其前兩個數字的總和。</span><span class="sxs-lookup"><span data-stu-id="4928d-161">Each next Fibonacci number is found by taking the sum of the previous two numbers.</span></span> <span data-ttu-id="4928d-162">新增下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="4928d-162">Add this code:</span></span>

```csharp
var previous = fibonacciNumbers[fibonacciNumbers.Count - 1];
var previous2 = fibonacciNumbers[fibonacciNumbers.Count - 2];

fibonacciNumbers.Add(previous + previous2);

foreach(var item in fibonacciNumbers)
    Console.WriteLine(item);
```

<span data-ttu-id="4928d-163">儲存檔案並輸入 `dotnet run` 來查看結果。</span><span class="sxs-lookup"><span data-stu-id="4928d-163">Save the file and type `dotnet run` to see the results.</span></span> 

> [!TIP]
> <span data-ttu-id="4928d-164">若要僅專注於本節的內容，您可以對呼叫 `WorkingWithStrings();` 的程式碼進行註解化。</span><span class="sxs-lookup"><span data-stu-id="4928d-164">To concentrate on just this section, you can comment out the code that calls `WorkingWithStrings();`.</span></span> <span data-ttu-id="4928d-165">請在該呼叫之前放置兩個 `/` 字元，例如：`// WorkingWithStrings();`。</span><span class="sxs-lookup"><span data-stu-id="4928d-165">Just put two `/` characters in front of the call like this:  `// WorkingWithStrings();`.</span></span> 

## <a name="challenge"></a><span data-ttu-id="4928d-166">挑戰</span><span class="sxs-lookup"><span data-stu-id="4928d-166">Challenge</span></span>
<span data-ttu-id="4928d-167">看看您是否可以結合運用來自此課程和先前課程的心得。</span><span class="sxs-lookup"><span data-stu-id="4928d-167">See if you can put together some of the lessons from this and earlier lessons.</span></span> <span data-ttu-id="4928d-168">請依費式數列數字，擴展您到目前為止所建立的內容。</span><span class="sxs-lookup"><span data-stu-id="4928d-168">Expand on what you've built so far with Fibonacci Numbers.</span></span> <span data-ttu-id="4928d-169">請嘗試將程式碼撰寫成可產生該數列的前 20 個數字。</span><span class="sxs-lookup"><span data-stu-id="4928d-169">Try and write the code to generate the first 20 numbers in the sequence.</span></span>

## <a name="complete-challenge"></a><span data-ttu-id="4928d-170">完成挑戰</span><span class="sxs-lookup"><span data-stu-id="4928d-170">Complete challenge</span></span>

<span data-ttu-id="4928d-171">您可以[在 GitHub 上查看完成的範例程式碼](https://github.com/dotnet/docs/tree/master/samples/csharp/list-quickstart/Program.cs) \(英文\) 來取得範例解決方案</span><span class="sxs-lookup"><span data-stu-id="4928d-171">You can see an example solution by [looking at the finished sample code on GitHub](https://github.com/dotnet/docs/tree/master/samples/csharp/list-quickstart/Program.cs)</span></span>

<span data-ttu-id="4928d-172">在迴圈每次反覆運算時，您都必須取清單中的最後兩個整數，將它們加總，並將該值新增至清單。</span><span class="sxs-lookup"><span data-stu-id="4928d-172">With each iteration of the loop, you're taking the last two integers in the list, summing them, and adding that value to the list.</span></span> <span data-ttu-id="4928d-173">迴圈會持續重複，直到將 20 個項目新增至清單為止。</span><span class="sxs-lookup"><span data-stu-id="4928d-173">The loop repeats until you've added 20 items to the list.</span></span>

<span data-ttu-id="4928d-174">恭喜，您已完成清單的教學課程。</span><span class="sxs-lookup"><span data-stu-id="4928d-174">Congratulations, you've completed the list tutorial.</span></span>

<span data-ttu-id="4928d-175">您可以在關於[集合](../../standard/collections/index.md)的 [.NET 指南](../../standard/index.md)主題中，深入了解 `List` 類型的使用方式。</span><span class="sxs-lookup"><span data-stu-id="4928d-175">You can learn more about working with the `List` type in the [.NET Guide](../../standard/index.md) topic on [collections](../../standard/collections/index.md).</span></span> <span data-ttu-id="4928d-176">您也能學習到許多其他的集合類型。</span><span class="sxs-lookup"><span data-stu-id="4928d-176">You'll also learn about many other collection types.</span></span>