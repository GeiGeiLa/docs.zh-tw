---
title: 單位類型 (F#)
description: 了解如何 F# 'unit' 類型通常用來保存其中值所需的語言語法所需或預期任何值時的位置。
ms.date: 05/16/2016
ms.openlocfilehash: c3dfa5f63c25a1e8abc0f75b905c129b311479af
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/02/2018
ms.locfileid: "44204652"
---
# <a name="unit-type"></a>單位類型

`unit`型別是一種類型，表示沒有特定的值;`unit`型別具有只能是單一數值，可做為預留位置，當沒有任何其他值，或不需要。

## <a name="syntax"></a>語法

```fsharp
// The value of the unit type.
()
```

## <a name="remarks"></a>備註

每個 F# 運算式必須評估為值。 不會產生值感興趣，類型的值，這個值的運算式`unit`用。 `unit`型別類似於`void`C# 和 c + + 等語言中的型別。

`unit`類型具有單一值，而該值由權杖`()`。

值`unit`類型通常會在 F# 程式設計語言語法中，需要值但所需或預期任何值時，保留位置。 可能的傳回值的範例。`printf`函式。 因為重要的動作`printf`作業發生在函數中，函式沒有傳回實際的值。 因此，傳回的值屬於類型`unit`。

某些建構預期`unit`值。 例如，`do`繫結或最上層模組的任何程式碼必須評估為`unit`值。 編譯器會回報警告時`do`繫結或最上層模組的程式碼產生的結果，而非`unit`未使用，如下列範例所示的值。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet901.fs)]

這項警告是功能性程式設計; 的特性它不會出現在其他.NET 程式設計語言。 在純綷功能性程式中，在其中函式沒有任何副作用，最終的傳回值會是唯一的函式呼叫的結果。 因此，結果會被忽略，時，可能的程式設計錯誤。 雖然 F# 不是純綷功能性程式設計語言，但最好還是遵循盡可能的功能性程式設計樣式。

## <a name="see-also"></a>另請參閱

- [基本](primitive-types.md)
- [F# 語言參考](index.md)
