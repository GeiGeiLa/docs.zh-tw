---
title: "抽象類別 (F#)"
description: "了解 F # 抽象類別，可保留未提供的部分或所有成員，然後代表通用的功能多樣的物件類型。"
keywords: "Visual F#, F#, 函式程式設計"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: a3dcc335-433b-4672-ac2d-ae6b11b816f3
ms.openlocfilehash: 209bcca70318db59506011b1f2bb74a09bf3814a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="abstract-classes"></a><span data-ttu-id="4d195-104">抽象類別</span><span class="sxs-lookup"><span data-stu-id="4d195-104">Abstract Classes</span></span>

<span data-ttu-id="4d195-105">*抽象類別*會保留未提供，部分或所有成員，如此可以由衍生類別中提供實作的類別。</span><span class="sxs-lookup"><span data-stu-id="4d195-105">*Abstract classes* are classes that leave some or all members unimplemented, so that implementations can be provided by derived classes.</span></span>

## <a name="syntax"></a><span data-ttu-id="4d195-106">語法</span><span class="sxs-lookup"><span data-stu-id="4d195-106">Syntax</span></span>

```fsharp
// Abstract class syntax.
[<AbstractClass>]
type [ accessibility-modifier ] abstract-class-name =
[ inherit base-class-or-interface-name ]
[ abstract-member-declarations-and-member-definitions ]

// Abstract member syntax.
abstract member member-name : type-signature
```

## <a name="remarks"></a><span data-ttu-id="4d195-107">備註</span><span class="sxs-lookup"><span data-stu-id="4d195-107">Remarks</span></span>
<span data-ttu-id="4d195-108">在物件導向程式設計中，抽象類別作為基底類別階層架構，並代表通用的功能多樣的物件類型。</span><span class="sxs-lookup"><span data-stu-id="4d195-108">In object-oriented programming, an abstract class is used as a base class of a hierarchy, and represents common functionality of a diverse set of object types.</span></span> <span data-ttu-id="4d195-109">名稱 「 抽象 」 一詞可知，抽象類別通常未對應到的問題領域中的具象實體直接。</span><span class="sxs-lookup"><span data-stu-id="4d195-109">As the name "abstract" implies, abstract classes often do not correspond directly onto concrete entities in the problem domain.</span></span> <span data-ttu-id="4d195-110">不過，它們並代表什麼許多不同的具象實體具有共通點。</span><span class="sxs-lookup"><span data-stu-id="4d195-110">However, they do represent what many different concrete entities have in common.</span></span>

<span data-ttu-id="4d195-111">抽象類別都必須有`AbstractClass`屬性。</span><span class="sxs-lookup"><span data-stu-id="4d195-111">Abstract classes must have the `AbstractClass` attribute.</span></span> <span data-ttu-id="4d195-112">他們可以實作和未提供的成員。</span><span class="sxs-lookup"><span data-stu-id="4d195-112">They can have implemented and unimplemented members.</span></span> <span data-ttu-id="4d195-113">使用詞彙的*抽象*時套用至類別是與其他.NET 語言; 相同不過，使用詞彙的*抽象*時套用至方法 （和屬性） 會稍有不同在 F # 從其在其他.NET 語言中使用。</span><span class="sxs-lookup"><span data-stu-id="4d195-113">The use of the term *abstract* when applied to a class is the same as in other .NET languages; however, the use of the term *abstract* when applied to methods (and properties) is a little different in F# from its use in other .NET languages.</span></span> <span data-ttu-id="4d195-114">在 F # 中，當方法會標示`abstract`關鍵字，這會指出成員有一個項目，稱為*虛擬分派插槽*，該類型的虛擬函式的內部資料表中。</span><span class="sxs-lookup"><span data-stu-id="4d195-114">In F#, when a method is marked with the `abstract` keyword, this indicates that a member has an entry, known as a *virtual dispatch slot*, in the internal table of virtual functions for that type.</span></span> <span data-ttu-id="4d195-115">換句話說，方法是虛擬的雖然`virtual`關鍵字不是 F # 語言中。</span><span class="sxs-lookup"><span data-stu-id="4d195-115">In other words, the method is virtual, although the `virtual` keyword is not used in the F# language.</span></span> <span data-ttu-id="4d195-116">關鍵字`abstract`不論方法是否實作虛擬方法上使用。</span><span class="sxs-lookup"><span data-stu-id="4d195-116">The keyword `abstract` is used on virtual methods regardless of whether the method is implemented.</span></span> <span data-ttu-id="4d195-117">該分派位置定義的是方法的虛擬的分派插槽的宣告。</span><span class="sxs-lookup"><span data-stu-id="4d195-117">The declaration of a virtual dispatch slot is separate from the definition of a method for that dispatch slot.</span></span> <span data-ttu-id="4d195-118">因此，F # 的虛擬方法宣告和定義在另一種.NET 語言中的相當的抽象方法宣告和不同的定義，其中一種組合`default`關鍵字或`override`關鍵字。</span><span class="sxs-lookup"><span data-stu-id="4d195-118">Therefore, the F# equivalent of a virtual method declaration and definition in another .NET language is a combination of both an abstract method declaration and a separate definition, with either the `default` keyword or the `override` keyword.</span></span> <span data-ttu-id="4d195-119">如需詳細資訊和範例，請參閱[方法](members/methods.md)。</span><span class="sxs-lookup"><span data-stu-id="4d195-119">For more information and examples, see [Methods](members/methods.md).</span></span>

<span data-ttu-id="4d195-120">類別會被視為只有在抽象方法已宣告但未定義抽象的。</span><span class="sxs-lookup"><span data-stu-id="4d195-120">A class is considered abstract only if there are abstract methods that are declared but not defined.</span></span> <span data-ttu-id="4d195-121">因此，具有抽象方法的類別不一定是抽象類別。</span><span class="sxs-lookup"><span data-stu-id="4d195-121">Therefore, classes that have abstract methods are not necessarily abstract classes.</span></span> <span data-ttu-id="4d195-122">除非類別具有未定義抽象方法，否則請勿使用**AbstractClass**屬性。</span><span class="sxs-lookup"><span data-stu-id="4d195-122">Unless a class has undefined abstract methods, do not use the **AbstractClass** attribute.</span></span>

<span data-ttu-id="4d195-123">在先前的語法，*存取範圍修飾詞*可以`public`，`private`或`internal`。</span><span class="sxs-lookup"><span data-stu-id="4d195-123">In the previous syntax, *accessibility-modifier* can be `public`, `private` or `internal`.</span></span> <span data-ttu-id="4d195-124">如需詳細資訊，請參閱[存取控制](access-control.md)。</span><span class="sxs-lookup"><span data-stu-id="4d195-124">For more information, see [Access Control](access-control.md).</span></span>

<span data-ttu-id="4d195-125">如同其他類型，基底類別和一或多個基底介面，可以有抽象類別。</span><span class="sxs-lookup"><span data-stu-id="4d195-125">As with other types, abstract classes can have a base class and one or more base interfaces.</span></span> <span data-ttu-id="4d195-126">每個基底類別或介面會出現在不同行搭配`inherit`關鍵字。</span><span class="sxs-lookup"><span data-stu-id="4d195-126">Each base class or interface appears on a separate line together with the `inherit` keyword.</span></span>

<span data-ttu-id="4d195-127">抽象類別的型別定義可以包含完整定義的成員，但它也可以包含抽象成員。</span><span class="sxs-lookup"><span data-stu-id="4d195-127">The type definition of an abstract class can contain fully defined members, but it can also contain abstract members.</span></span> <span data-ttu-id="4d195-128">先前語法中分別顯示抽象成員的語法。</span><span class="sxs-lookup"><span data-stu-id="4d195-128">The syntax for abstract members is shown separately in the previous syntax.</span></span> <span data-ttu-id="4d195-129">在此語法中，*類型簽章*成員的清單，其中包含的參數類型的順序和傳回型別，以分隔`->`語彙基元和/或`*`的局部調用視語彙基元和採用 tuple 形式參數。</span><span class="sxs-lookup"><span data-stu-id="4d195-129">In this syntax, the *type signature* of a member is a list that contains the parameter types in order and the return types, separated by `->` tokens and/or `*` tokens as appropriate for curried and tupled parameters.</span></span> <span data-ttu-id="4d195-130">抽象成員的類型簽章的語法是相同簽章檔案中使用，而且在 Visual Studio 程式碼編輯器中 intellisense 所示。</span><span class="sxs-lookup"><span data-stu-id="4d195-130">The syntax for abstract member type signatures is the same as that used in signature files and that shown by IntelliSense in the Visual Studio Code Editor.</span></span>

<span data-ttu-id="4d195-131">下列程式碼說明具有兩個非抽象衍生的類別，Square 和圓形的形狀的抽象類別。</span><span class="sxs-lookup"><span data-stu-id="4d195-131">The following code illustrates an abstract class Shape, which has two non-abstract derived classes, Square and Circle.</span></span> <span data-ttu-id="4d195-132">此範例示範如何使用抽象類別、 方法和屬性。</span><span class="sxs-lookup"><span data-stu-id="4d195-132">The example shows how to use abstract classes, methods, and properties.</span></span> <span data-ttu-id="4d195-133">在範例中，圖形的抽象類別代表的具象實體圓形和正方形的常見項目。</span><span class="sxs-lookup"><span data-stu-id="4d195-133">In the example, the abstract class Shape represents the common elements of the concrete entities circle and square.</span></span> <span data-ttu-id="4d195-134">（在二維座標系統中） 的所有形狀的常見功能會縮小圖形類別抽象： 方格、 旋轉的角度和區域和周邊屬性上的位置。</span><span class="sxs-lookup"><span data-stu-id="4d195-134">The common features of all shapes (in a two-dimensional coordinate system) are abstracted out into the Shape class: the position on the grid, an angle of rotation, and the area and perimeter properties.</span></span> <span data-ttu-id="4d195-135">這些可以被覆寫，除了位置，其中個別圖形不能變更的行為。</span><span class="sxs-lookup"><span data-stu-id="4d195-135">These can be overridden, except for position, the behavior of which individual shapes cannot change.</span></span>

<span data-ttu-id="4d195-136">旋轉方法可以覆寫，如同圓形類別，這是因為其對稱性旋轉而異。</span><span class="sxs-lookup"><span data-stu-id="4d195-136">The rotation method can be overridden, as in the Circle class, which is rotation invariant because of its symmetry.</span></span> <span data-ttu-id="4d195-137">因此在圓形類別中，不做任何動作的方法取代旋轉方法。</span><span class="sxs-lookup"><span data-stu-id="4d195-137">So in the Circle class, the rotation method is replaced by a method that does nothing.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2901.fs)]

<span data-ttu-id="4d195-138">**輸出：**</span><span class="sxs-lookup"><span data-stu-id="4d195-138">**Output:**</span></span>

```
Perimeter of square with side length 10.000000 is 40.000000
Circumference of circle with radius 5.000000 is 31.415927
Area of Square: 100.000000
Area of Circle: 78.539816
```

## <a name="see-also"></a><span data-ttu-id="4d195-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4d195-139">See Also</span></span>
[<span data-ttu-id="4d195-140">類別</span><span class="sxs-lookup"><span data-stu-id="4d195-140">Classes</span></span>](classes.md)

[<span data-ttu-id="4d195-141">成員</span><span class="sxs-lookup"><span data-stu-id="4d195-141">Members</span></span>](members/index.md)

[<span data-ttu-id="4d195-142">方法</span><span class="sxs-lookup"><span data-stu-id="4d195-142">Methods</span></span>](members/methods.md)

[<span data-ttu-id="4d195-143">屬性</span><span class="sxs-lookup"><span data-stu-id="4d195-143">Properties</span></span>](members/Properties.md)