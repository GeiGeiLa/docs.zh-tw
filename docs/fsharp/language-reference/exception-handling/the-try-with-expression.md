---
title: 例外狀況：try...with 運算式 (F#)
description: 了解如何使用 例外狀況處理 F# 'try...with' 運算式。
ms.date: 05/16/2016
ms.openlocfilehash: 588960c0f8ccedb431c37d0f1314bf1a293b638c
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/02/2018
ms.locfileid: "44042162"
---
# <a name="exceptions-the-trywith-expression"></a>例外狀況：try...with 運算式

本主題描述`try...with`運算式，用於在 F# 語言中處理的例外狀況的運算式。

## <a name="syntax"></a>語法

```fsharp
try
    expression1
with
| pattern1 -> expression2
| pattern2 -> expression3
...
```

## <a name="remarks"></a>備註

`try...with`運算式用來處理在 F# 中的例外狀況。 類似於`try...catch`C# 中的陳述式。 在上述語法中中的程式碼*expression1*可能產生例外狀況。 `try...with`運算式傳回的值。 如果擲不回任何例外狀況，整個運算式會傳回的值*expression1*。 如果發生例外狀況，每個*圖樣*例外狀況，以及針對對應的第一個模式比對會依次比較*運算式*，稱為*例外狀況處理常式*，則請針對該分支會執行，並整體的運算式傳回運算式的值在該例外狀況處理常式。 如果沒有模式會比對，在呼叫堆疊會傳播例外狀況，直到找到相符的處理常式。 傳回例外狀況處理常式中的每個運算式的值的型別必須符合的運算式傳回的型別`try`區塊。

通常，也發生錯誤，這表示沒有有效的值從每個例外狀況處理常式中的運算式可傳回。 常見的模式是將運算式的型別是選項類型。 下列程式碼範例將示範這個模式。

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5601.fs)]

例外狀況可以是.NET 例外狀況，或者可以是 F# 例外狀況。 您可以使用，以定義 F# 例外狀況`exception`關鍵字。

您可以使用各種不同的模式，若要篩選的例外狀況類型和其他條件;下表摘要說明選項。

|模式|描述|
|-------|-----------|
|:? *例外狀況類型*|比對指定的.NET 例外狀況類型。|
|:? *例外狀況型別*做為*識別碼*|符合指定的.NET 例外狀況類型，但可讓例外狀況的已命名的值。|
|*例外狀況名稱*(*引數*)|比對的 F# 例外狀況類型並繫結引數。|
|*identifier*|符合任何例外狀況和繫結至例外狀況物件的名稱。 相當於 **： 嗎？System.Exception 為 * * * 識別碼*|
|*識別項*當*條件*|如果條件為 true 會比對任何例外狀況。|

## <a name="examples"></a>範例

下列程式碼範例說明使用各種不同例外狀況處理常式模式。

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5602.fs)]

>[!NOTE]
`try...with`建構是從個別運算式`try...finally`運算式。 因此，如果您的程式碼需要兩`with`區塊和`finally`區塊中，您必須將巢狀化兩個運算式。

>[!NOTE]
您可以使用`try...with`中的非同步工作流程和其他計算運算式，在其中案例的自訂的版本`try...with`運算式的使用方式。 如需詳細資訊，請參閱 <<c0> [ 非同步工作流程](../asynchronous-workflows.md)，並[計算運算式](../computation-expressions.md)。

## <a name="see-also"></a>另請參閱

- [例外狀況處理](index.md)
- [例外狀況類型](exception-types.md)
- [例外狀況：`try...finally` 運算式](the-try-finally-expression.md)
