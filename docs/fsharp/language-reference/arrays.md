---
title: "陣列 (F#)"
description: "了解如何建立和使用 F # 程式語言中的陣列。"
keywords: "Visual F#, F#, 函式程式設計"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 61fa9084-abdc-4cf5-8213-91ec1211866b
ms.openlocfilehash: 7c9d8405230f4d765d3afdeaa154ddc598d0d1ec
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="arrays"></a><span data-ttu-id="4e1f5-104">陣列</span><span class="sxs-lookup"><span data-stu-id="4e1f5-104">Arrays</span></span>

> [!NOTE]
<span data-ttu-id="4e1f5-105">API 參考連結將帶您前往 MSDN。</span><span class="sxs-lookup"><span data-stu-id="4e1f5-105">The API reference link will take you to MSDN.</span></span>  <span data-ttu-id="4e1f5-106">docs.microsoft.com API 參考不完整。</span><span class="sxs-lookup"><span data-stu-id="4e1f5-106">The docs.microsoft.com API reference is not complete.</span></span>

<span data-ttu-id="4e1f5-107">陣列是屬於相同類型的所有連續的資料元素的固定大小，以零為起始的可變動集合。</span><span class="sxs-lookup"><span data-stu-id="4e1f5-107">Arrays are fixed-size, zero-based, mutable collections of consecutive data elements that are all of the same type.</span></span>

## <a name="creating-arrays"></a><span data-ttu-id="4e1f5-108">建立陣列</span><span class="sxs-lookup"><span data-stu-id="4e1f5-108">Creating Arrays</span></span>
<span data-ttu-id="4e1f5-109">您可以數種方式來建立陣列。</span><span class="sxs-lookup"><span data-stu-id="4e1f5-109">You can create arrays in several ways.</span></span> <span data-ttu-id="4e1f5-110">您可以藉由列出之間的連續值建立小型陣列`[|`和`|]`並以分號分隔，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="4e1f5-110">You can create a small array by listing consecutive values between `[|` and `|]` and separated by semicolons, as shown in the following examples.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet1.fs)]

<span data-ttu-id="4e1f5-111">您也可以將每個項目放在不同行，則這個分號分隔符號是選擇性。</span><span class="sxs-lookup"><span data-stu-id="4e1f5-111">You can also put each element on a separate line, in which case the semicolon separator is optional.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet2.fs)]

<span data-ttu-id="4e1f5-112">陣列元素的類型推斷將使用常值，而且必須一致。</span><span class="sxs-lookup"><span data-stu-id="4e1f5-112">The type of the array elements is inferred from the literals used and must be consistent.</span></span> <span data-ttu-id="4e1f5-113">下列程式碼會導致錯誤，因為 1.0 是浮點數與 2 和 3 是整數。</span><span class="sxs-lookup"><span data-stu-id="4e1f5-113">The following code causes an error because 1.0 is a float and 2 and 3 are integers.</span></span>

```fsharp
// Causes an error.
// let array2 = [| 1.0; 2; 3 |]
```

<span data-ttu-id="4e1f5-114">您也可以使用循序項運算式來建立陣列。</span><span class="sxs-lookup"><span data-stu-id="4e1f5-114">You can also use sequence expressions to create arrays.</span></span> <span data-ttu-id="4e1f5-115">以下為範例，會整數平方的陣列建立從 1 到 10。</span><span class="sxs-lookup"><span data-stu-id="4e1f5-115">Following is an example that creates an array of squares of integers from 1 to 10.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet3.fs)]

<span data-ttu-id="4e1f5-116">若要建立的陣列中所有的元素會初始化為零，請使用`Array.zeroCreate`。</span><span class="sxs-lookup"><span data-stu-id="4e1f5-116">To create an array in which all the elements are initialized to zero, use `Array.zeroCreate`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet4.fs)]
    
## <a name="accessing-elements"></a><span data-ttu-id="4e1f5-117">存取項目</span><span class="sxs-lookup"><span data-stu-id="4e1f5-117">Accessing Elements</span></span>

<span data-ttu-id="4e1f5-118">您可以使用點運算子來存取陣列元素 (`.`) 和括號 (`[`和`]`)。</span><span class="sxs-lookup"><span data-stu-id="4e1f5-118">You can access array elements by using a dot operator (`.`) and brackets (`[` and `]`).</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet5.fs)]

<span data-ttu-id="4e1f5-119">陣列索引從 0 開始。</span><span class="sxs-lookup"><span data-stu-id="4e1f5-119">Array indexes start at 0.</span></span>

<span data-ttu-id="4e1f5-120">您也可以使用切割標記法，可讓您指定子陣列的範圍，以存取陣列項目。</span><span class="sxs-lookup"><span data-stu-id="4e1f5-120">You can also access array elements by using slice notation, which enables you to specify a subrange of the array.</span></span> <span data-ttu-id="4e1f5-121">配量標記法的範例如下。</span><span class="sxs-lookup"><span data-stu-id="4e1f5-121">Examples of slice notation follow.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet51.fs)]

<span data-ttu-id="4e1f5-122">使用切割標記法時，會建立新陣列的複本。</span><span class="sxs-lookup"><span data-stu-id="4e1f5-122">When slice notation is used, a new copy of the array is created.</span></span>


## <a name="array-types-and-modules"></a><span data-ttu-id="4e1f5-123">陣列類型和模組</span><span class="sxs-lookup"><span data-stu-id="4e1f5-123">Array Types and Modules</span></span>
<span data-ttu-id="4e1f5-124">所有的 F # 陣列的類型是.NET Framework 型別<xref:System.Array?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="4e1f5-124">The type of all F# arrays is the .NET Framework type <xref:System.Array?displayProperty=nameWithType>.</span></span> <span data-ttu-id="4e1f5-125">因此，F # 陣列支援中所提供的所有功能<xref:System.Array?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="4e1f5-125">Therefore, F# arrays support all the functionality available in <xref:System.Array?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="4e1f5-126">程式庫模組[ `Microsoft.FSharp.Collections.Array` ](https://msdn.microsoft.com/library/0cda8040-9396-40dd-8dcd-cf48542165a1)支援一維陣列上的作業。</span><span class="sxs-lookup"><span data-stu-id="4e1f5-126">The library module [`Microsoft.FSharp.Collections.Array`](https://msdn.microsoft.com/library/0cda8040-9396-40dd-8dcd-cf48542165a1) supports operations on one-dimensional arrays.</span></span> <span data-ttu-id="4e1f5-127">模組`Array2D`， `Array3D`，和`Array4D`包含支援兩個、 三和四個維度，在陣列上的作業分別函式。</span><span class="sxs-lookup"><span data-stu-id="4e1f5-127">The modules `Array2D`, `Array3D`, and `Array4D` contain functions that support operations on arrays of two, three, and four dimensions, respectively.</span></span> <span data-ttu-id="4e1f5-128">您可以建立陣列的陣序規範大於 4 使用<xref:System.Array?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="4e1f5-128">You can create arrays of rank greater than four by using <xref:System.Array?displayProperty=nameWithType>.</span></span>

### <a name="simple-functions"></a><span data-ttu-id="4e1f5-129">簡單函式</span><span class="sxs-lookup"><span data-stu-id="4e1f5-129">Simple Functions</span></span>
<span data-ttu-id="4e1f5-130">[`Array.get`](https://msdn.microsoft.com/library/dd93e85d-7e80-4d76-8de0-b6d45bcf07bc)取得項目。</span><span class="sxs-lookup"><span data-stu-id="4e1f5-130">[`Array.get`](https://msdn.microsoft.com/library/dd93e85d-7e80-4d76-8de0-b6d45bcf07bc) gets an element.</span></span> <span data-ttu-id="4e1f5-131">[`Array.length`](https://msdn.microsoft.com/library/0d775b6a-4a8f-4bd1-83e5-843b3251725f)提供陣列的長度。</span><span class="sxs-lookup"><span data-stu-id="4e1f5-131">[`Array.length`](https://msdn.microsoft.com/library/0d775b6a-4a8f-4bd1-83e5-843b3251725f) gives the length of an array.</span></span> <span data-ttu-id="4e1f5-132">[`Array.set`](https://msdn.microsoft.com/library/847edc0d-4dc5-4a39-98c7-d4320c60e790)設定為指定值的項目。</span><span class="sxs-lookup"><span data-stu-id="4e1f5-132">[`Array.set`](https://msdn.microsoft.com/library/847edc0d-4dc5-4a39-98c7-d4320c60e790) sets an element to a specified value.</span></span> <span data-ttu-id="4e1f5-133">下列程式碼範例說明如何使用這些函式。</span><span class="sxs-lookup"><span data-stu-id="4e1f5-133">The following code example illustrates the use of these functions.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet9.fs)]

<span data-ttu-id="4e1f5-134">輸出如下。</span><span class="sxs-lookup"><span data-stu-id="4e1f5-134">The output is as follows.</span></span>

```
0 1 2 3 4 5 6 7 8 9
```

### <a name="functions-that-create-arrays"></a><span data-ttu-id="4e1f5-135">建立陣列的函式</span><span class="sxs-lookup"><span data-stu-id="4e1f5-135">Functions That Create Arrays</span></span>

<span data-ttu-id="4e1f5-136">幾個函式會建立陣列，而不需要現有的陣列。</span><span class="sxs-lookup"><span data-stu-id="4e1f5-136">Several functions create arrays without requiring an existing array.</span></span> <span data-ttu-id="4e1f5-137">[`Array.empty`](https://msdn.microsoft.com/library/c3694b92-1c16-4c54-9bf2-fe398fadce32)建立新的陣列不包含任何項目。</span><span class="sxs-lookup"><span data-stu-id="4e1f5-137">[`Array.empty`](https://msdn.microsoft.com/library/c3694b92-1c16-4c54-9bf2-fe398fadce32) creates a new array that does not contain any elements.</span></span> <span data-ttu-id="4e1f5-138">[`Array.create`](https://msdn.microsoft.com/library/e848c8d6-1142-4080-9727-8dacc26066be)建立指定大小的陣列，並將所有項目設定為提供的值。</span><span class="sxs-lookup"><span data-stu-id="4e1f5-138">[`Array.create`](https://msdn.microsoft.com/library/e848c8d6-1142-4080-9727-8dacc26066be) creates an array of a specified size and sets all the elements to provided values.</span></span> <span data-ttu-id="4e1f5-139">[`Array.init`](https://msdn.microsoft.com/library/ee898089-63b0-40aa-910c-5ae7e32f6665)建立陣列，指定維度與函式來產生項目。</span><span class="sxs-lookup"><span data-stu-id="4e1f5-139">[`Array.init`](https://msdn.microsoft.com/library/ee898089-63b0-40aa-910c-5ae7e32f6665) creates an array, given a dimension and a function to generate the elements.</span></span> <span data-ttu-id="4e1f5-140">[`Array.zeroCreate`](https://msdn.microsoft.com/library/fa5b8e7a-1b5b-411c-8622-b58d7a14d3b2)建立的陣列中的所有項目會初始化為零的值為陣列的型別。</span><span class="sxs-lookup"><span data-stu-id="4e1f5-140">[`Array.zeroCreate`](https://msdn.microsoft.com/library/fa5b8e7a-1b5b-411c-8622-b58d7a14d3b2) creates an array in which all the elements are initialized to the zero value for the array's type.</span></span> <span data-ttu-id="4e1f5-141">下列程式碼會示範這些函式。</span><span class="sxs-lookup"><span data-stu-id="4e1f5-141">The following code demonstrates these functions.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet91.fs)]

<span data-ttu-id="4e1f5-142">輸出如下。</span><span class="sxs-lookup"><span data-stu-id="4e1f5-142">The output is as follows.</span></span>

```
Length of empty array: 0
Area of floats set to 5.0: [|5.0; 5.0; 5.0; 5.0; 5.0; 5.0; 5.0; 5.0; 5.0; 5.0|]
Array of squares: [|0; 1; 4; 9; 16; 25; 36; 49; 64; 81|]
```

<span data-ttu-id="4e1f5-143">[`Array.copy`](https://msdn.microsoft.com/library/9d0202f1-1ea0-475e-9d66-4f8ccc3c5b5f)建立新的陣列，其中包含從現有的陣列複製的項目。</span><span class="sxs-lookup"><span data-stu-id="4e1f5-143">[`Array.copy`](https://msdn.microsoft.com/library/9d0202f1-1ea0-475e-9d66-4f8ccc3c5b5f) creates a new array that contains elements that are copied from an existing array.</span></span> <span data-ttu-id="4e1f5-144">請注意，此複本的淺層複本，這表示如果項目類型是參考類型，則複製只參考而非基礎物件。</span><span class="sxs-lookup"><span data-stu-id="4e1f5-144">Note that the copy is a shallow copy, which means that if the element type is a reference type, only the reference is copied, not the underlying object.</span></span> <span data-ttu-id="4e1f5-145">下列程式碼範例會說明這點。</span><span class="sxs-lookup"><span data-stu-id="4e1f5-145">The following code example illustrates this.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet11.fs)]

<span data-ttu-id="4e1f5-146">上述程式碼的輸出如下所示：</span><span class="sxs-lookup"><span data-stu-id="4e1f5-146">The output of the preceding code is as follows:</span></span>

```
[|Test1; Test2; |]
[|; Test2; |]
```

<span data-ttu-id="4e1f5-147">字串`Test1`只會出現在第一個陣列建立新的項目作業覆寫中的參考，因為`firstArray`但不會影響原始參考為空字串，仍存在於`secondArray`。</span><span class="sxs-lookup"><span data-stu-id="4e1f5-147">The string `Test1` appears only in the first array because the operation of creating a new element overwrites the reference in `firstArray` but does not affect the original reference to an empty string that is still present in `secondArray`.</span></span> <span data-ttu-id="4e1f5-148">字串`Test2`顯示在兩個陣列，因為`Insert`作業<xref:System.Text.StringBuilder?displayProperty=nameWithType>類型會影響基礎<xref:System.Text.StringBuilder?displayProperty=nameWithType>中兩個陣列參考的物件。</span><span class="sxs-lookup"><span data-stu-id="4e1f5-148">The string `Test2` appears in both arrays because the `Insert` operation on the <xref:System.Text.StringBuilder?displayProperty=nameWithType> type affects the underlying <xref:System.Text.StringBuilder?displayProperty=nameWithType> object, which is referenced in both arrays.</span></span>

<span data-ttu-id="4e1f5-149">[`Array.sub`](https://msdn.microsoft.com/library/40fb12ba-41d7-4ef0-b33a-56727deeef9d)從陣列中的子範圍中產生新的陣列。</span><span class="sxs-lookup"><span data-stu-id="4e1f5-149">[`Array.sub`](https://msdn.microsoft.com/library/40fb12ba-41d7-4ef0-b33a-56727deeef9d) generates a new array from a subrange of an array.</span></span> <span data-ttu-id="4e1f5-150">您可以提供起始的索引和長度指定做為子範圍。</span><span class="sxs-lookup"><span data-stu-id="4e1f5-150">You specify the subrange by providing the starting index and the length.</span></span> <span data-ttu-id="4e1f5-151">下列程式碼示範 `Array.sub` 的用法。</span><span class="sxs-lookup"><span data-stu-id="4e1f5-151">The following code demonstrates the use of `Array.sub`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet12.fs)]

<span data-ttu-id="4e1f5-152">輸出會顯示子陣列開始項目 5，而且包含 10 個元素。</span><span class="sxs-lookup"><span data-stu-id="4e1f5-152">The output shows that the subarray starts at element 5 and contains 10 elements.</span></span>

```
[|5; 6; 7; 8; 9; 10; 11; 12; 13; 14|]
```
<span data-ttu-id="4e1f5-153">[`Array.append`](https://msdn.microsoft.com/library/08836310-5036-4474-b9a2-2c73e2293911)藉由結合兩個現有的陣列建立新的陣列。</span><span class="sxs-lookup"><span data-stu-id="4e1f5-153">[`Array.append`](https://msdn.microsoft.com/library/08836310-5036-4474-b9a2-2c73e2293911) creates a new array by combining two existing arrays.</span></span>

<span data-ttu-id="4e1f5-154">下列程式碼示範**Array.append**。</span><span class="sxs-lookup"><span data-stu-id="4e1f5-154">The following code demonstrates **Array.append**.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet13.fs)]

<span data-ttu-id="4e1f5-155">上述程式碼的輸出如下所示。</span><span class="sxs-lookup"><span data-stu-id="4e1f5-155">The output of the preceding code is as follows.</span></span>

```
[|1; 2; 3; 4; 5; 6|]
```

<span data-ttu-id="4e1f5-156">[`Array.choose`](https://msdn.microsoft.com/library/f5c8a5e2-637f-44d4-b35c-be96a6618b09)選取要在新的陣列包含陣列的項目。</span><span class="sxs-lookup"><span data-stu-id="4e1f5-156">[`Array.choose`](https://msdn.microsoft.com/library/f5c8a5e2-637f-44d4-b35c-be96a6618b09) selects elements of an array to include in a new array.</span></span> <span data-ttu-id="4e1f5-157">下列程式碼示範`Array.choose`。</span><span class="sxs-lookup"><span data-stu-id="4e1f5-157">The following code demonstrates `Array.choose`.</span></span> <span data-ttu-id="4e1f5-158">請注意，陣列的項目類型並沒有比對選項類型中傳回的值類型。</span><span class="sxs-lookup"><span data-stu-id="4e1f5-158">Note that the element type of the array does not have to match the type of the value returned in the option type.</span></span> <span data-ttu-id="4e1f5-159">在此範例中，項目類型是`int`且選項多項式函式的結果`elem*elem - 1`，做為浮點數。</span><span class="sxs-lookup"><span data-stu-id="4e1f5-159">In this example, the element type is `int` and the option is the result of a polynomial function, `elem*elem - 1`, as a floating point number.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet14.fs)]

<span data-ttu-id="4e1f5-160">上述程式碼的輸出如下所示。</span><span class="sxs-lookup"><span data-stu-id="4e1f5-160">The output of the preceding code is as follows.</span></span>

```
[|3.0; 15.0; 35.0; 63.0; 99.0|]
```

<span data-ttu-id="4e1f5-161">[`Array.collect`](https://msdn.microsoft.com/library/c3b60c3b-9455-48c9-bc2b-e88f0434342a)現有陣列的每個陣列項目上執行指定的函式和收集函式所產生的項目，然後將它們合併成新的陣列。</span><span class="sxs-lookup"><span data-stu-id="4e1f5-161">[`Array.collect`](https://msdn.microsoft.com/library/c3b60c3b-9455-48c9-bc2b-e88f0434342a) runs a specified function on each array element of an existing array and then collects the elements generated by the function and combines them into a new array.</span></span> <span data-ttu-id="4e1f5-162">下列程式碼示範`Array.collect`。</span><span class="sxs-lookup"><span data-stu-id="4e1f5-162">The following code demonstrates `Array.collect`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet15.fs)]

<span data-ttu-id="4e1f5-163">上述程式碼的輸出如下所示。</span><span class="sxs-lookup"><span data-stu-id="4e1f5-163">The output of the preceding code is as follows.</span></span>

```
[|0; 1; 0; 1; 2; 3; 4; 5; 0; 1; 2; 3; 4; 5; 6; 7; 8; 9; 10|]
```

<span data-ttu-id="4e1f5-164">[`Array.concat`](https://msdn.microsoft.com/library/f7219b79-1ec8-4a25-96b1-edbedb358302)會接受一連串的陣列，並將它們合併成單一陣列。</span><span class="sxs-lookup"><span data-stu-id="4e1f5-164">[`Array.concat`](https://msdn.microsoft.com/library/f7219b79-1ec8-4a25-96b1-edbedb358302) takes a sequence of arrays and combines them into a single array.</span></span> <span data-ttu-id="4e1f5-165">下列程式碼示範`Array.concat`。</span><span class="sxs-lookup"><span data-stu-id="4e1f5-165">The following code demonstrates `Array.concat`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet16.fs)]

<span data-ttu-id="4e1f5-166">上述程式碼的輸出如下所示。</span><span class="sxs-lookup"><span data-stu-id="4e1f5-166">The output of the preceding code is as follows.</span></span>

```
[|(1, 1, 1); (1, 2, 2); (1, 3, 3); (2, 1, 2); (2, 2, 4); (2, 3, 6); (3, 1, 3);
(3, 2, 6); (3, 3, 9)|]
```

<span data-ttu-id="4e1f5-167">[`Array.filter`](https://msdn.microsoft.com/library/b885b214-47fc-4639-9664-b8c183a39ede)會採用布林條件函式，並產生包含這些條件為 true 的輸入陣列中項目的新陣列。</span><span class="sxs-lookup"><span data-stu-id="4e1f5-167">[`Array.filter`](https://msdn.microsoft.com/library/b885b214-47fc-4639-9664-b8c183a39ede) takes a Boolean condition function and generates a new array that contains only those elements from the input array for which the condition is true.</span></span> <span data-ttu-id="4e1f5-168">下列程式碼示範`Array.filter`。</span><span class="sxs-lookup"><span data-stu-id="4e1f5-168">The following code demonstrates `Array.filter`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet17.fs)]

<span data-ttu-id="4e1f5-169">上述程式碼的輸出如下所示。</span><span class="sxs-lookup"><span data-stu-id="4e1f5-169">The output of the preceding code is as follows.</span></span>

```
[|2; 4; 6; 8; 10|]
```

<span data-ttu-id="4e1f5-170">[`Array.rev`](https://msdn.microsoft.com/library/1bbf822c-763b-4794-af21-97d2e48ef709)藉由反轉現有陣列的順序來產生新的陣列。</span><span class="sxs-lookup"><span data-stu-id="4e1f5-170">[`Array.rev`](https://msdn.microsoft.com/library/1bbf822c-763b-4794-af21-97d2e48ef709) generates a new array by reversing the order of an existing array.</span></span> <span data-ttu-id="4e1f5-171">下列程式碼示範`Array.rev`。</span><span class="sxs-lookup"><span data-stu-id="4e1f5-171">The following code demonstrates `Array.rev`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet18.fs)]  

<span data-ttu-id="4e1f5-172">上述程式碼的輸出如下所示。</span><span class="sxs-lookup"><span data-stu-id="4e1f5-172">The output of the preceding code is as follows.</span></span>

```
"Hello world!"
```

<span data-ttu-id="4e1f5-173">您可以輕鬆地結合陣列模組中的函數，可將陣列轉換會使用管線運算子 (`|>`)，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="4e1f5-173">You can easily combine functions in the array module that transform arrays by using the pipeline operator (`|>`), as shown in the following example.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet19.fs)]

<span data-ttu-id="4e1f5-174">輸出為</span><span class="sxs-lookup"><span data-stu-id="4e1f5-174">The output is</span></span>

```
[|100; 36; 16; 4|]
```

### <a name="multidimensional-arrays"></a><span data-ttu-id="4e1f5-175">多維陣列</span><span class="sxs-lookup"><span data-stu-id="4e1f5-175">Multidimensional Arrays</span></span>

<span data-ttu-id="4e1f5-176">您可以建立多維度陣列，但是沒有其他語法會寫入多維度陣列常值。</span><span class="sxs-lookup"><span data-stu-id="4e1f5-176">A multidimensional array can be created, but there is no syntax for writing a multidimensional array literal.</span></span> <span data-ttu-id="4e1f5-177">使用運算子[ `array2D` ](https://msdn.microsoft.com/library/1d52503d-2990-49fc-8fd3-6b0e508aa236)從序列的陣列元素的序列建立陣列。</span><span class="sxs-lookup"><span data-stu-id="4e1f5-177">Use the operator [`array2D`](https://msdn.microsoft.com/library/1d52503d-2990-49fc-8fd3-6b0e508aa236) to create an array from a sequence of sequences of array elements.</span></span> <span data-ttu-id="4e1f5-178">序列可以是陣列或清單常值。</span><span class="sxs-lookup"><span data-stu-id="4e1f5-178">The sequences can be array or list literals.</span></span> <span data-ttu-id="4e1f5-179">例如，下列程式碼會建立二維陣列。</span><span class="sxs-lookup"><span data-stu-id="4e1f5-179">For example, the following code creates a two-dimensional array.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet20.fs)]

<span data-ttu-id="4e1f5-180">您也可以使用此函式[ `Array2D.init` ](https://msdn.microsoft.com/library/9de07e95-bc21-4927-b5b4-08fdec882c7b)來初始化陣列的兩個維度，以及類似函式可供使用的三個和第四個維度的陣列。</span><span class="sxs-lookup"><span data-stu-id="4e1f5-180">You can also use the function [`Array2D.init`](https://msdn.microsoft.com/library/9de07e95-bc21-4927-b5b4-08fdec882c7b) to initialize arrays of two dimensions, and similar functions are available for arrays of three and four dimensions.</span></span> <span data-ttu-id="4e1f5-181">這些函式可接受函式是用來建立項目。</span><span class="sxs-lookup"><span data-stu-id="4e1f5-181">These functions take a function that is used to create the elements.</span></span> <span data-ttu-id="4e1f5-182">若要建立二維陣列，包含項目設為初始的值，而不是指定函式，請使用[ `Array2D.create` ](https://msdn.microsoft.com/library/36c9d980-b241-4a20-bc64-bcfa0205d804)函式，也適用於陣列最多 4 個維度。</span><span class="sxs-lookup"><span data-stu-id="4e1f5-182">To create a two-dimensional array that contains elements set to an initial value instead of specifying a function, use the [`Array2D.create`](https://msdn.microsoft.com/library/36c9d980-b241-4a20-bc64-bcfa0205d804) function, which is also available for arrays up to four dimensions.</span></span> <span data-ttu-id="4e1f5-183">下列程式碼範例首先顯示如何建立陣列的陣列，包含所需的項目，並接著會使用`Array2D.init`來產生所需的二維陣列。</span><span class="sxs-lookup"><span data-stu-id="4e1f5-183">The following code example first shows how to create an array of arrays that contain the desired elements, and then uses `Array2D.init` to generate the desired two-dimensional array.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet21.fs)]

<span data-ttu-id="4e1f5-184">陣列陣序規範 4 到支援的陣列編製索引及配量語法。</span><span class="sxs-lookup"><span data-stu-id="4e1f5-184">Array indexing and slicing syntax is supported for arrays up to rank 4.</span></span> <span data-ttu-id="4e1f5-185">當您在多個維度中指定索引時，您使用逗號來分隔索引，如下列程式碼範例所示。</span><span class="sxs-lookup"><span data-stu-id="4e1f5-185">When you specify an index in multiple dimensions, you use commas to separate the indexes, as illustrated in the following code example.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet22.fs)]
    
<span data-ttu-id="4e1f5-186">二維陣列的型別寫出做為`<type>[,]`(例如， `int[,]`， `double[,]`)，和三維陣列的類型撰寫為`<type>[,,]`，對高維度的陣列。</span><span class="sxs-lookup"><span data-stu-id="4e1f5-186">The type of a two-dimensional array is written out as `<type>[,]` (for example, `int[,]`, `double[,]`), and the type of a three-dimensional array is written as `<type>[,,]`, and so on for arrays of higher dimensions.</span></span>

<span data-ttu-id="4e1f5-187">一維陣列的可用功能的子集也適用於多維度陣列。</span><span class="sxs-lookup"><span data-stu-id="4e1f5-187">Only a subset of the functions available for one-dimensional arrays is also available for multidimensional arrays.</span></span> <span data-ttu-id="4e1f5-188">如需詳細資訊，請參閱[ `Collections.Array Module` ](https://msdn.microsoft.com/visualfsharpdocs/conceptual/collections.array-module-%5bfsharp%5d)， [ `Collections.Array2D Module` ](https://msdn.microsoft.com/visualfsharpdocs/conceptual/collections.array2d-module-%5bfsharp%5d)， [ `Collections.Array3D Module` ](https://msdn.microsoft.com/visualfsharpdocs/conceptual/collections.array3d-module-%5bfsharp%5d)，和[ `Collections.Array4D Module` ](https://msdn.microsoft.com/visualfsharpdocs/conceptual/collections.array4d-module-%5bfsharp%5d)。</span><span class="sxs-lookup"><span data-stu-id="4e1f5-188">For more information, see [`Collections.Array Module`](https://msdn.microsoft.com/visualfsharpdocs/conceptual/collections.array-module-%5bfsharp%5d), [`Collections.Array2D Module`](https://msdn.microsoft.com/visualfsharpdocs/conceptual/collections.array2d-module-%5bfsharp%5d), [`Collections.Array3D Module`](https://msdn.microsoft.com/visualfsharpdocs/conceptual/collections.array3d-module-%5bfsharp%5d), and [`Collections.Array4D Module`](https://msdn.microsoft.com/visualfsharpdocs/conceptual/collections.array4d-module-%5bfsharp%5d).</span></span>

### <a name="array-slicing-and-multidimensional-arrays"></a><span data-ttu-id="4e1f5-189">陣列配量和多維度陣列</span><span class="sxs-lookup"><span data-stu-id="4e1f5-189">Array Slicing and Multidimensional Arrays</span></span>

<span data-ttu-id="4e1f5-190">在二維陣列 （矩陣） 中，您可以藉由指定範圍，並使用萬用字元擷取子矩陣 (`*`) 字元來指定整個資料列或資料行。</span><span class="sxs-lookup"><span data-stu-id="4e1f5-190">In a two-dimensional array (a matrix), you can extract a sub-matrix by specifying ranges and using a wildcard (`*`) character to specify whole rows or columns.</span></span>

```fsharp
/ Get rows 1 to N from an NxM matrix (returns a matrix):
matrix.[1.., *]

// Get rows 1 to 3 from a matrix (returns a matrix):
matrix.[1..3, *]

// Get columns 1 to 3 from a matrix (returns a matrix):
matrix.[*, 1..3]

// Get a 3x3 submatrix:
matrix.[1..3, 1..3]
```

<span data-ttu-id="4e1f5-191">為準，F # 3.1，您可以將多維度陣列分解成相同或更低之維度的子陣列。</span><span class="sxs-lookup"><span data-stu-id="4e1f5-191">As of F# 3.1, you can decompose a multidimensional array into subarrays of the same or lower dimension.</span></span> <span data-ttu-id="4e1f5-192">例如，您也可以指定單一資料列或資料行，以取得向量從一個矩陣。</span><span class="sxs-lookup"><span data-stu-id="4e1f5-192">For example, you can obtain a vector from a matrix by specifying a single row or column.</span></span>

```fsharp
// Get row 3 from a matrix as a vector:
matrix.[3, *]

// Get column 3 from a matrix as a vector:
matrix.[*, 3]
```

<span data-ttu-id="4e1f5-193">您可以使用這個配量的類型會實作項目存取運算子，以及多載語法`GetSlice`方法。</span><span class="sxs-lookup"><span data-stu-id="4e1f5-193">You can use this slicing syntax for types that implement the element access operators and overloaded `GetSlice` methods.</span></span> <span data-ttu-id="4e1f5-194">例如，下列程式碼會建立包裝 F # 2 維陣列，實作提供支援陣列編製索引，項目屬性，並實作三個版本的矩陣類型`GetSlice`。</span><span class="sxs-lookup"><span data-stu-id="4e1f5-194">For example, the following code creates a Matrix type that wraps the F# 2D array, implements an Item property to provide support for array indexing, and implements three versions of `GetSlice`.</span></span> <span data-ttu-id="4e1f5-195">如果您可以使用這段程式碼做為範本，為您的矩陣類型，您可以使用本章節描述的所有分割作業。</span><span class="sxs-lookup"><span data-stu-id="4e1f5-195">If you can use this code as a template for your matrix types, you can use all the slicing operations that this section describes.</span></span>

```fsharp
type Matrix<'T>(N: int, M: int) =
    let internalArray = Array2D.zeroCreate<'T> N M

    member this.Item
        with get(a: int, b: int) = internalArray.[a, b]
        and set(a: int, b: int) (value:'T) = internalArray.[a, b] <- value

    member this.GetSlice(rowStart: int option, rowFinish : int option, colStart: int option, colFinish : int option) =
        let rowStart = 
            match rowStart with
            | Some(v) -> v
            | None -> 0
        let rowFinish =
            match rowFinish with
            | Some(v) -> v
            | None -> internalArray.GetLength(0) - 1
        let colStart = 
            match colStart with
            | Some(v) -> v
            | None -> 0
        let colFinish = 
            match colFinish with
            | Some(v) -> v
            | None -> internalArray.GetLength(1) - 1
        internalArray.[rowStart..rowFinish, colStart..colFinish]

    member this.GetSlice(row: int, colStart: int option, colFinish: int option) =
        let colStart = 
            match colStart with
            | Some(v) -> v
            | None -> 0
        let colFinish = 
            match colFinish with
            | Some(v) -> v
            | None -> internalArray.GetLength(1) - 1
        internalArray.[row, colStart..colFinish]

    member this.GetSlice(rowStart: int option, rowFinish: int option, col: int) =
        let rowStart = 
            match rowStart with
            | Some(v) -> v
            | None -> 0
        let rowFinish = 
            match rowFinish with
            | Some(v) -> v
            | None -> internalArray.GetLength(0) - 1
        internalArray.[rowStart..rowFinish, col]

module test =
    let generateTestMatrix x y =
        let matrix = new Matrix<float>(3, 3)
        for i in 0..2 do
            for j in 0..2 do
                matrix.[i, j] <- float(i) * x - float(j) * y
        matrix

    let test1 = generateTestMatrix 2.3 1.1
    let submatrix = test1.[0..1, 0..1]
    printfn "%A" submatrix

    let firstRow = test1.[0,*]
    let secondRow = test1.[1,*]
    let firstCol = test1.[*,0]
    printfn "%A" firstCol
```

### <a name="boolean-functions-on-arrays"></a><span data-ttu-id="4e1f5-196">在陣列上的布林函數</span><span class="sxs-lookup"><span data-stu-id="4e1f5-196">Boolean Functions on Arrays</span></span>

<span data-ttu-id="4e1f5-197">函式[ `Array.exists` ](https://msdn.microsoft.com/library/8e47ad6c-c065-4876-8cb4-ec960ec3e5c9)和[ `Array.exists2` ](https://msdn.microsoft.com/library/2e384a6a-f99d-4e23-b677-250ffbc1dd8e)分別測試在一個或兩個陣列中的項目。</span><span class="sxs-lookup"><span data-stu-id="4e1f5-197">The functions [`Array.exists`](https://msdn.microsoft.com/library/8e47ad6c-c065-4876-8cb4-ec960ec3e5c9) and [`Array.exists2`](https://msdn.microsoft.com/library/2e384a6a-f99d-4e23-b677-250ffbc1dd8e) test elements in either one or two arrays, respectively.</span></span> <span data-ttu-id="4e1f5-198">這些函式採用測試函式，並傳回`true`如果沒有項目 (或項目組`Array.exists2`)，可滿足條件。</span><span class="sxs-lookup"><span data-stu-id="4e1f5-198">These functions take a test function and return `true` if there is an element (or element pair for `Array.exists2`) that satisfies the condition.</span></span>

<span data-ttu-id="4e1f5-199">下列程式碼會示範如何使用`Array.exists`和`Array.exists2`。</span><span class="sxs-lookup"><span data-stu-id="4e1f5-199">The following code demonstrates the use of `Array.exists` and `Array.exists2`.</span></span> <span data-ttu-id="4e1f5-200">在這些範例中，新的函式會建立所套用的引數，在這些情況下，函式引數的其中之一。</span><span class="sxs-lookup"><span data-stu-id="4e1f5-200">In these examples, new functions are created by applying only one of the arguments, in these cases, the function argument.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet23.fs)]

<span data-ttu-id="4e1f5-201">上述程式碼的輸出如下所示。</span><span class="sxs-lookup"><span data-stu-id="4e1f5-201">The output of the preceding code is as follows.</span></span>

```
true
false
false
true
```

<span data-ttu-id="4e1f5-202">同樣地，函式[ `Array.forall` ](https://msdn.microsoft.com/library/d88f2cd0-fa7f-45cf-ac15-31eae9086cc4)測試以判斷每個項目是否符合布林條件的陣列。</span><span class="sxs-lookup"><span data-stu-id="4e1f5-202">Similarly, the function [`Array.forall`](https://msdn.microsoft.com/library/d88f2cd0-fa7f-45cf-ac15-31eae9086cc4) tests an array to determine whether every element satisfies a Boolean condition.</span></span> <span data-ttu-id="4e1f5-203">變化[ `Array.forall2` ](https://msdn.microsoft.com/library/c68f61a1-030c-4024-b705-c4768b6c96b9)使用布林函數，包括兩個陣列的長度相等的項目進行相同的工作。</span><span class="sxs-lookup"><span data-stu-id="4e1f5-203">The variation [`Array.forall2`](https://msdn.microsoft.com/library/c68f61a1-030c-4024-b705-c4768b6c96b9) does the same thing by using a Boolean function that involves elements of two arrays of equal length.</span></span> <span data-ttu-id="4e1f5-204">下列程式碼說明如何使用這些函式。</span><span class="sxs-lookup"><span data-stu-id="4e1f5-204">The following code illustrates the use of these functions.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet24.fs)]

<span data-ttu-id="4e1f5-205">這些範例的輸出如下所示。</span><span class="sxs-lookup"><span data-stu-id="4e1f5-205">The output for these examples is as follows.</span></span>

```
false
true
true
false
```

### <a name="searching-arrays"></a><span data-ttu-id="4e1f5-206">搜尋陣列</span><span class="sxs-lookup"><span data-stu-id="4e1f5-206">Searching Arrays</span></span>

<span data-ttu-id="4e1f5-207">[`Array.find`](https://msdn.microsoft.com/library/db6d920a-de19-4520-85a4-d83de77c1b33)會採用布林值的函式，並傳回第一個元素的函式會傳回`true`，或是引發<xref:System.Collections.Generic.KeyNotFoundException?displayProperty=nameWithType>如果找到符合的條件沒有任何項目。</span><span class="sxs-lookup"><span data-stu-id="4e1f5-207">[`Array.find`](https://msdn.microsoft.com/library/db6d920a-de19-4520-85a4-d83de77c1b33) takes a Boolean function and returns the first element for which the function returns `true`, or raises a <xref:System.Collections.Generic.KeyNotFoundException?displayProperty=nameWithType> if no element that satisfies the condition is found.</span></span> <span data-ttu-id="4e1f5-208">[`Array.findIndex`](https://msdn.microsoft.com/library/5ae3a8f9-7b8f-44ea-a740-d5700f4d899f)就像`Array.find`，只不過它會傳回而不是項目本身的項目索引。</span><span class="sxs-lookup"><span data-stu-id="4e1f5-208">[`Array.findIndex`](https://msdn.microsoft.com/library/5ae3a8f9-7b8f-44ea-a740-d5700f4d899f) is like `Array.find`, except that it returns the index of the element instead of the element itself.</span></span>

<span data-ttu-id="4e1f5-209">下列程式碼會使用`Array.find`和`Array.findIndex`找出的數字是正方形和完美的 cube。</span><span class="sxs-lookup"><span data-stu-id="4e1f5-209">The following code uses `Array.find` and `Array.findIndex` to locate a number that is both a perfect square and perfect cube.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet25.fs)]

<span data-ttu-id="4e1f5-210">輸出如下。</span><span class="sxs-lookup"><span data-stu-id="4e1f5-210">The output is as follows.</span></span>

```
The first element that is both a square and a cube is 64 and its index is 62.
```

<span data-ttu-id="4e1f5-211">[`Array.tryFind`](https://msdn.microsoft.com/library/7bd65f6c-df77-454c-ac3a-6f7baecec9d9)就像`Array.find`，只不過其結果是選項類型，並傳回`None`如果不找到任何項目。</span><span class="sxs-lookup"><span data-stu-id="4e1f5-211">[`Array.tryFind`](https://msdn.microsoft.com/library/7bd65f6c-df77-454c-ac3a-6f7baecec9d9) is like `Array.find`, except that its result is an option type, and it returns `None` if no element is found.</span></span> <span data-ttu-id="4e1f5-212">`Array.tryFind`應該使用而不是`Array.find`時您不知道相符的項目是否為陣列。</span><span class="sxs-lookup"><span data-stu-id="4e1f5-212">`Array.tryFind` should be used instead of `Array.find` when you do not know whether a matching element is in the array.</span></span> <span data-ttu-id="4e1f5-213">同樣地， [ `Array.tryFindIndex` ](https://msdn.microsoft.com/library/da82f7fe-95e9-4fd5-a924-cd3c9d10618a)就像是[ `Array.findIndex` ](https://msdn.microsoft.com/library/5ae3a8f9-7b8f-44ea-a740-d5700f4d899f)不同之處在於選項類型為傳回的值。</span><span class="sxs-lookup"><span data-stu-id="4e1f5-213">Similarly, [`Array.tryFindIndex`](https://msdn.microsoft.com/library/da82f7fe-95e9-4fd5-a924-cd3c9d10618a) is like [`Array.findIndex`](https://msdn.microsoft.com/library/5ae3a8f9-7b8f-44ea-a740-d5700f4d899f) except that the option type is the return value.</span></span> <span data-ttu-id="4e1f5-214">如果不找到任何元素，則選項`None`。</span><span class="sxs-lookup"><span data-stu-id="4e1f5-214">If no element is found, the option is `None`.</span></span>

<span data-ttu-id="4e1f5-215">下列程式碼示範 `Array.tryFind` 的用法。</span><span class="sxs-lookup"><span data-stu-id="4e1f5-215">The following code demonstrates the use of `Array.tryFind`.</span></span> <span data-ttu-id="4e1f5-216">此程式碼視先前的程式碼而定。</span><span class="sxs-lookup"><span data-stu-id="4e1f5-216">This code depends on the previous code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet26.fs)]

<span data-ttu-id="4e1f5-217">輸出如下。</span><span class="sxs-lookup"><span data-stu-id="4e1f5-217">The output is as follows.</span></span>

```
Found an element: 1
Found an element: 729
```

<span data-ttu-id="4e1f5-218">使用[ `Array.tryPick` ](https://msdn.microsoft.com/library/72d45f85-037b-43a9-97fd-17239f72713e)當需要轉換除了找不到項目。</span><span class="sxs-lookup"><span data-stu-id="4e1f5-218">Use [`Array.tryPick`](https://msdn.microsoft.com/library/72d45f85-037b-43a9-97fd-17239f72713e) when you need to transform an element in addition to finding it.</span></span> <span data-ttu-id="4e1f5-219">結果是，此函數會傳回已轉換的項目，做為選項值，為第一個項目或`None`如果找到這類項目。</span><span class="sxs-lookup"><span data-stu-id="4e1f5-219">The result is the first element for which the function returns the transformed element as an option value, or `None` if no such element is found.</span></span>

<span data-ttu-id="4e1f5-220">下列程式碼示範 `Array.tryPick` 的用法。</span><span class="sxs-lookup"><span data-stu-id="4e1f5-220">The following code shows the use of `Array.tryPick`.</span></span> <span data-ttu-id="4e1f5-221">在此情況下，而不是 lambda 運算式，數個本機 helper 函式定義來簡化程式碼。</span><span class="sxs-lookup"><span data-stu-id="4e1f5-221">In this case, instead of a lambda expression, several local helper functions are defined to simplify the code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet27.fs)]

<span data-ttu-id="4e1f5-222">輸出如下。</span><span class="sxs-lookup"><span data-stu-id="4e1f5-222">The output is as follows.</span></span>

```
Found an element 1 with square root 1 and cube root 1.
Found an element 64 with square root 8 and cube root 4.
Found an element 729 with square root 27 and cube root 9.
Found an element 4096 with square root 64 and cube root 16.
```

### <a name="performing-computations-on-arrays"></a><span data-ttu-id="4e1f5-223">在陣列上執行計算</span><span class="sxs-lookup"><span data-stu-id="4e1f5-223">Performing Computations on Arrays</span></span>

<span data-ttu-id="4e1f5-224">[ `Array.average` ](https://msdn.microsoft.com/library/7029f2b9-91ea-41cb-be1b-466a5a0db20e)函式傳回陣列中的每個項目的平均值。</span><span class="sxs-lookup"><span data-stu-id="4e1f5-224">The [`Array.average`](https://msdn.microsoft.com/library/7029f2b9-91ea-41cb-be1b-466a5a0db20e) function returns the average of each element in an array.</span></span> <span data-ttu-id="4e1f5-225">它會限制項目類型，可支援完全除數的整數，包含浮點類型，但不是整數類資料類型。</span><span class="sxs-lookup"><span data-stu-id="4e1f5-225">It is limited to element types that support exact division by an integer, which includes floating point types but not integral types.</span></span> <span data-ttu-id="4e1f5-226">[ `Array.averageBy` ](https://msdn.microsoft.com/library/e9d64609-06a3-48f0-bc07-226ab0f85c54)函式傳回之結果的每個項目上呼叫函式的平均。</span><span class="sxs-lookup"><span data-stu-id="4e1f5-226">The [`Array.averageBy`](https://msdn.microsoft.com/library/e9d64609-06a3-48f0-bc07-226ab0f85c54) function returns the average of the results of calling a function on each element.</span></span> <span data-ttu-id="4e1f5-227">整數類資料類型的陣列，您可以使用`Array.averageBy`而且具有函式，將每個項目轉換成浮點計算的類型。</span><span class="sxs-lookup"><span data-stu-id="4e1f5-227">For an array of integral type, you can use `Array.averageBy` and have the function convert each element to a floating point type for the computation.</span></span>

<span data-ttu-id="4e1f5-228">使用[ `Array.max` ](https://msdn.microsoft.com/library/f03fbda0-fce6-40e2-a85d-79c9d81f710b)或[ `Array.min` ](https://msdn.microsoft.com/library/d6b3da5f-bac0-4355-9846-4b72d95bc3fd)取得的最大或最小項目，如果項目型別支援它。</span><span class="sxs-lookup"><span data-stu-id="4e1f5-228">Use [`Array.max`](https://msdn.microsoft.com/library/f03fbda0-fce6-40e2-a85d-79c9d81f710b) or [`Array.min`](https://msdn.microsoft.com/library/d6b3da5f-bac0-4355-9846-4b72d95bc3fd) to get the maximum or minimum element, if the element type supports it.</span></span> <span data-ttu-id="4e1f5-229">同樣地， [ `Array.maxBy` ](https://msdn.microsoft.com/library/18dbe7c5-482e-4766-8e01-12a76f847045)和[ `Array.minBy` ](https://msdn.microsoft.com/library/24091583-be78-4cc9-9fab-de6d7506af4f)讓函式先執行，或許是為了支援比較類型轉換。</span><span class="sxs-lookup"><span data-stu-id="4e1f5-229">Similarly, [`Array.maxBy`](https://msdn.microsoft.com/library/18dbe7c5-482e-4766-8e01-12a76f847045) and [`Array.minBy`](https://msdn.microsoft.com/library/24091583-be78-4cc9-9fab-de6d7506af4f) allow a function to be executed first, perhaps to transform to a type that supports comparison.</span></span>

<span data-ttu-id="4e1f5-230">[`Array.sum`](https://msdn.microsoft.com/library/4ffdb8c8-cd94-4b0b-9e5c-a7c9c17963c2)新增陣列的項目和[ `Array.sumBy` ](https://msdn.microsoft.com/library/41698ba6-1adc-4169-8cc5-7a0e3f8de56b)每個項目上呼叫的函式，並將相加的結果。</span><span class="sxs-lookup"><span data-stu-id="4e1f5-230">[`Array.sum`](https://msdn.microsoft.com/library/4ffdb8c8-cd94-4b0b-9e5c-a7c9c17963c2) adds the elements of an array, and [`Array.sumBy`](https://msdn.microsoft.com/library/41698ba6-1adc-4169-8cc5-7a0e3f8de56b) calls a function on each element and adds the results together.</span></span>

<span data-ttu-id="4e1f5-231">若要在陣列中每個項目上執行函式，而不儲存傳回值，使用[ `Array.iter` ](https://msdn.microsoft.com/library/94eba0f1-ecd7-459f-b89f-ed2a2923e516)。</span><span class="sxs-lookup"><span data-stu-id="4e1f5-231">To execute a function on each element in an array without storing the return values, use [`Array.iter`](https://msdn.microsoft.com/library/94eba0f1-ecd7-459f-b89f-ed2a2923e516).</span></span> <span data-ttu-id="4e1f5-232">對於牽涉到兩個陣列的長度相等的函式，使用[ `Array.iter2` ](https://msdn.microsoft.com/library/018aa9b9-f186-4142-be8a-a62462794fdc)。</span><span class="sxs-lookup"><span data-stu-id="4e1f5-232">For a function involving two arrays of equal length, use [`Array.iter2`](https://msdn.microsoft.com/library/018aa9b9-f186-4142-be8a-a62462794fdc).</span></span> <span data-ttu-id="4e1f5-233">如果您也要保留一個陣列的函式的結果，請使用[ `Array.map` ](https://msdn.microsoft.com/library/38cbe824-0480-47be-85fd-df3afdd97a45)或[ `Array.map2` ](https://msdn.microsoft.com/library/bb7aafe8-4a1f-45b9-92fc-1af9eafbea5c)，一次在兩個陣列上操作。</span><span class="sxs-lookup"><span data-stu-id="4e1f5-233">If you also need to keep an array of the results of the function, use [`Array.map`](https://msdn.microsoft.com/library/38cbe824-0480-47be-85fd-df3afdd97a45) or [`Array.map2`](https://msdn.microsoft.com/library/bb7aafe8-4a1f-45b9-92fc-1af9eafbea5c), which operates on two arrays at a time.</span></span>

<span data-ttu-id="4e1f5-234">這些變化[ `Array.iteri` ](https://msdn.microsoft.com/library/8bbe2ed4-ada7-4906-ac3e-cb09f9db6486)和[ `Array.iteri2` ](https://msdn.microsoft.com/library/c041b91f-6080-45b7-867b-2ed983a90405)允許要參與計算之項目的索引; 也適用於[ `Array.mapi` ](https://msdn.microsoft.com/library/f7e45994-b0a1-49e6-8fb5-5641cea8fde4)和[ `Array.mapi2` ](https://msdn.microsoft.com/library/5edb33d2-47da-44e1-9290-40c00c47d5b0)。</span><span class="sxs-lookup"><span data-stu-id="4e1f5-234">The variations [`Array.iteri`](https://msdn.microsoft.com/library/8bbe2ed4-ada7-4906-ac3e-cb09f9db6486) and [`Array.iteri2`](https://msdn.microsoft.com/library/c041b91f-6080-45b7-867b-2ed983a90405) allow the index of the element to be involved in the computation; the same is true for [`Array.mapi`](https://msdn.microsoft.com/library/f7e45994-b0a1-49e6-8fb5-5641cea8fde4) and [`Array.mapi2`](https://msdn.microsoft.com/library/5edb33d2-47da-44e1-9290-40c00c47d5b0).</span></span>

<span data-ttu-id="4e1f5-235">函式[ `Array.fold` ](https://msdn.microsoft.com/library/5ed9dd3b-3694-4567-94d0-fd9a24474e09)， [ `Array.foldBack` ](https://msdn.microsoft.com/library/1121a453-dead-4711-a0ca-cc147752989c)， [ `Array.reduce` ](https://msdn.microsoft.com/library/fd62a985-89fe-4f49-a9d4-0c808ac6749d)， [ `Array.reduceBack` ](https://msdn.microsoft.com/library/4fdd4cbe-2238-4c5c-b286-597a7e9036f9)， [`Array.scan` ](https://msdn.microsoft.com/library/f6893608-9146-450d-9ebb-a0016803fbb0)，和[ `Array.scanBack` ](https://msdn.microsoft.com/library/7610f406-7a5c-41db-a0ca-8e2a2a4826ad)執行牽涉到陣列的所有元素的演算法。</span><span class="sxs-lookup"><span data-stu-id="4e1f5-235">The functions [`Array.fold`](https://msdn.microsoft.com/library/5ed9dd3b-3694-4567-94d0-fd9a24474e09), [`Array.foldBack`](https://msdn.microsoft.com/library/1121a453-dead-4711-a0ca-cc147752989c), [`Array.reduce`](https://msdn.microsoft.com/library/fd62a985-89fe-4f49-a9d4-0c808ac6749d), [`Array.reduceBack`](https://msdn.microsoft.com/library/4fdd4cbe-2238-4c5c-b286-597a7e9036f9), [`Array.scan`](https://msdn.microsoft.com/library/f6893608-9146-450d-9ebb-a0016803fbb0), and [`Array.scanBack`](https://msdn.microsoft.com/library/7610f406-7a5c-41db-a0ca-8e2a2a4826ad) execute algorithms that involve all the elements of an array.</span></span> <span data-ttu-id="4e1f5-236">同樣地，變化[ `Array.fold2` ](https://msdn.microsoft.com/library/5c845087-d041-476e-8cc4-53ae6849ef79)和[ `Array.foldBack2` ](https://msdn.microsoft.com/library/aa51b405-df20-4c51-9998-a6530f7db862)的兩個陣列執行運算。</span><span class="sxs-lookup"><span data-stu-id="4e1f5-236">Similarly, the variations [`Array.fold2`](https://msdn.microsoft.com/library/5c845087-d041-476e-8cc4-53ae6849ef79) and [`Array.foldBack2`](https://msdn.microsoft.com/library/aa51b405-df20-4c51-9998-a6530f7db862) perform computations on two arrays.</span></span>

<span data-ttu-id="4e1f5-237">執行計算的這些函式對應至函式中相同名稱的[List 模組](https://msdn.microsoft.com/library/a2264ba3-2d45-40dd-9040-4f7aa2ad9788)。</span><span class="sxs-lookup"><span data-stu-id="4e1f5-237">These functions for performing computations correspond to the functions of the same name in the [List module](https://msdn.microsoft.com/library/a2264ba3-2d45-40dd-9040-4f7aa2ad9788).</span></span> <span data-ttu-id="4e1f5-238">如需使用方式範例，請參閱[列出](lists.md)。</span><span class="sxs-lookup"><span data-stu-id="4e1f5-238">For usage examples, see [Lists](lists.md).</span></span>

### <a name="modifying-arrays"></a><span data-ttu-id="4e1f5-239">修改陣列</span><span class="sxs-lookup"><span data-stu-id="4e1f5-239">Modifying Arrays</span></span>

<span data-ttu-id="4e1f5-240">[`Array.set`](https://msdn.microsoft.com/library/847edc0d-4dc5-4a39-98c7-d4320c60e790)設定為指定值的項目。</span><span class="sxs-lookup"><span data-stu-id="4e1f5-240">[`Array.set`](https://msdn.microsoft.com/library/847edc0d-4dc5-4a39-98c7-d4320c60e790) sets an element to a specified value.</span></span> <span data-ttu-id="4e1f5-241">[`Array.fill`](https://msdn.microsoft.com/library/c83c9886-81d9-44f9-a195-61c7b87f7df2)設定為指定值陣列中的項目範圍。</span><span class="sxs-lookup"><span data-stu-id="4e1f5-241">[`Array.fill`](https://msdn.microsoft.com/library/c83c9886-81d9-44f9-a195-61c7b87f7df2) sets a range of elements in an array to a specified value.</span></span> <span data-ttu-id="4e1f5-242">下列程式碼提供的範例`Array.fill`。</span><span class="sxs-lookup"><span data-stu-id="4e1f5-242">The following code provides an example of `Array.fill`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet28.fs)]

<span data-ttu-id="4e1f5-243">輸出如下。</span><span class="sxs-lookup"><span data-stu-id="4e1f5-243">The output is as follows.</span></span>

```
[|1; 2; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 23; 24; 25|]
```

<span data-ttu-id="4e1f5-244">您可以使用[ `Array.blit` ](https://msdn.microsoft.com/library/675e13e4-7fb9-4e0d-a5be-a112830de667)来複製的子區段的一個陣列至另一個陣列。</span><span class="sxs-lookup"><span data-stu-id="4e1f5-244">You can use [`Array.blit`](https://msdn.microsoft.com/library/675e13e4-7fb9-4e0d-a5be-a112830de667) to copy a subsection of one array to another array.</span></span>

### <a name="converting-to-and-from-other-types"></a><span data-ttu-id="4e1f5-245">從其他類型轉換</span><span class="sxs-lookup"><span data-stu-id="4e1f5-245">Converting to and from Other Types</span></span>

<span data-ttu-id="4e1f5-246">[`Array.ofList`](https://msdn.microsoft.com/library/e7225239-f561-45a4-b0b5-69a1cdcae78b)從清單建立陣列。</span><span class="sxs-lookup"><span data-stu-id="4e1f5-246">[`Array.ofList`](https://msdn.microsoft.com/library/e7225239-f561-45a4-b0b5-69a1cdcae78b) creates an array from a list.</span></span> <span data-ttu-id="4e1f5-247">[`Array.ofSeq`](https://msdn.microsoft.com/library/6bedf5e0-4b22-46da-b09c-6aa09eff220c)從序列建立陣列。</span><span class="sxs-lookup"><span data-stu-id="4e1f5-247">[`Array.ofSeq`](https://msdn.microsoft.com/library/6bedf5e0-4b22-46da-b09c-6aa09eff220c) creates an array from a sequence.</span></span> <span data-ttu-id="4e1f5-248">[`Array.toList`](https://msdn.microsoft.com/library/4deff724-0be4-4688-92e7-9d67a1097786)和[ `Array.toSeq` ](https://msdn.microsoft.com/library/ac28dbab-406c-4fe0-ab08-c1ce5e247af4)從陣列類型轉換成這些集合類型。</span><span class="sxs-lookup"><span data-stu-id="4e1f5-248">[`Array.toList`](https://msdn.microsoft.com/library/4deff724-0be4-4688-92e7-9d67a1097786) and [`Array.toSeq`](https://msdn.microsoft.com/library/ac28dbab-406c-4fe0-ab08-c1ce5e247af4) convert to these other collection types from the array type.</span></span>

### <a name="sorting-arrays"></a><span data-ttu-id="4e1f5-249">排序陣列</span><span class="sxs-lookup"><span data-stu-id="4e1f5-249">Sorting Arrays</span></span>

<span data-ttu-id="4e1f5-250">使用[ `Array.sort` ](https://msdn.microsoft.com/library/c6679075-e7eb-463c-9be5-c89be140c312)排序陣列使用泛型比較函式。</span><span class="sxs-lookup"><span data-stu-id="4e1f5-250">Use [`Array.sort`](https://msdn.microsoft.com/library/c6679075-e7eb-463c-9be5-c89be140c312) to sort an array by using the generic comparison function.</span></span> <span data-ttu-id="4e1f5-251">使用[ `Array.sortBy` ](https://msdn.microsoft.com/library/144498dc-091d-4575-a229-c0bcbd61426b)為指定的函式會產生一個值，稱為*金鑰*，以使用泛型比較函式的索引鍵上排序。</span><span class="sxs-lookup"><span data-stu-id="4e1f5-251">Use [`Array.sortBy`](https://msdn.microsoft.com/library/144498dc-091d-4575-a229-c0bcbd61426b) to specify a function that generates a value, referred to as a *key*, to sort by using the generic comparison function on the key.</span></span> <span data-ttu-id="4e1f5-252">使用[ `Array.sortWith` ](https://msdn.microsoft.com/library/699d3638-4244-4f42-8496-45f53d43ce95)如果您想要提供自訂比較函式。</span><span class="sxs-lookup"><span data-stu-id="4e1f5-252">Use [`Array.sortWith`](https://msdn.microsoft.com/library/699d3638-4244-4f42-8496-45f53d43ce95) if you want to provide a custom comparison function.</span></span> <span data-ttu-id="4e1f5-253">`Array.sort``Array.sortBy`，和`Array.sortWith`所有傳回的已排序的陣列做為新的陣列。</span><span class="sxs-lookup"><span data-stu-id="4e1f5-253">`Array.sort`, `Array.sortBy`, and `Array.sortWith` all return the sorted array as a new array.</span></span> <span data-ttu-id="4e1f5-254">這些變化[ `Array.sortInPlace` ](https://msdn.microsoft.com/library/36f39947-8a88-4823-9e9b-e9d838d292e0)， [ `Array.sortInPlaceBy` ](https://msdn.microsoft.com/library/7fb9d2dd-d461-4c67-8b43-b5c59fc12c3f)，和[ `Array.sortInPlaceWith` ](https://msdn.microsoft.com/library/454f9e11-972d-47a6-a854-8031cb0c7b0b)修改現有的陣列，而不是傳回新的。</span><span class="sxs-lookup"><span data-stu-id="4e1f5-254">The variations [`Array.sortInPlace`](https://msdn.microsoft.com/library/36f39947-8a88-4823-9e9b-e9d838d292e0), [`Array.sortInPlaceBy`](https://msdn.microsoft.com/library/7fb9d2dd-d461-4c67-8b43-b5c59fc12c3f), and [`Array.sortInPlaceWith`](https://msdn.microsoft.com/library/454f9e11-972d-47a6-a854-8031cb0c7b0b) modify the existing array instead of returning a new one.</span></span>

### <a name="arrays-and-tuples"></a><span data-ttu-id="4e1f5-255">陣列和 Tuple</span><span class="sxs-lookup"><span data-stu-id="4e1f5-255">Arrays and Tuples</span></span>

<span data-ttu-id="4e1f5-256">函式[ `Array.zip` ](https://msdn.microsoft.com/library/23e086b8-b266-4db2-8b68-e88e6a8e2187)和[ `Array.unzip` ](https://msdn.microsoft.com/library/a529b47c-2e2b-4f79-ad44-c578432d2f48) tuple 配對的陣列轉換成 tuple 的陣列，反之亦然。</span><span class="sxs-lookup"><span data-stu-id="4e1f5-256">The functions [`Array.zip`](https://msdn.microsoft.com/library/23e086b8-b266-4db2-8b68-e88e6a8e2187) and [`Array.unzip`](https://msdn.microsoft.com/library/a529b47c-2e2b-4f79-ad44-c578432d2f48) convert arrays of tuple pairs to tuples of arrays and vice versa.</span></span> <span data-ttu-id="4e1f5-257">[`Array.zip3`](https://msdn.microsoft.com/library/1745744a-d2ca-4c3e-b825-3f15d9f4000d)和[ `Array.unzip3` ](https://msdn.microsoft.com/library/bc3e6db0-f334-444f-8c30-813942880677)很相似，不同之處在於它們使用三個元素的 tuple 或三個陣列的 tuple。</span><span class="sxs-lookup"><span data-stu-id="4e1f5-257">[`Array.zip3`](https://msdn.microsoft.com/library/1745744a-d2ca-4c3e-b825-3f15d9f4000d) and [`Array.unzip3`](https://msdn.microsoft.com/library/bc3e6db0-f334-444f-8c30-813942880677) are similar except that they work with tuples of three elements or tuples of three arrays.</span></span>

## <a name="parallel-computations-on-arrays"></a><span data-ttu-id="4e1f5-258">在陣列上的平行運算</span><span class="sxs-lookup"><span data-stu-id="4e1f5-258">Parallel Computations on Arrays</span></span>

<span data-ttu-id="4e1f5-259">模組[ `Array.Parallel` ](https://msdn.microsoft.com/library/60f30b77-5af4-4050-9a5c-bcdb3f5cbb09)包含在陣列上執行平行計算的函式。</span><span class="sxs-lookup"><span data-stu-id="4e1f5-259">The module [`Array.Parallel`](https://msdn.microsoft.com/library/60f30b77-5af4-4050-9a5c-bcdb3f5cbb09) contains functions for performing parallel computations on arrays.</span></span> <span data-ttu-id="4e1f5-260">無法在以.NET Framework 版本 4 之前的版本為目標的應用程式中使用此模組。</span><span class="sxs-lookup"><span data-stu-id="4e1f5-260">This module is not available in applications that target versions of the .NET Framework prior to version 4.</span></span>

## <a name="see-also"></a><span data-ttu-id="4e1f5-261">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4e1f5-261">See Also</span></span>
[<span data-ttu-id="4e1f5-262">F# 語言參考</span><span class="sxs-lookup"><span data-stu-id="4e1f5-262">F# Language Reference</span></span>](index.md)

[<span data-ttu-id="4e1f5-263">F # 中;型別</span><span class="sxs-lookup"><span data-stu-id="4e1f5-263">F#; Types</span></span>](fsharp-types.md)