# mojo語言基本(.mojo或.🔥)

## 架構
- #介紹
- #mojo的運行
- #語彙結構
  - #var&let
- #註解方式
- #型別
  - #Int與int的差別
- #變數
  - #命名規定
- #運算式及運算元
  - #運算式
  - #運算元
- #述句
- #迴圈
  - #forloop
  - #while
  - #do-while
  - #forEach
  - #while及do-while之差異
- #物件
  - #陣列
- #函式
- #struct
- #例外處理
  - #例外介紹
  - #處理例外
- #表單
- #註解及參見
  - #關鍵保留字 一覽

## #介紹
Mojo 是一種與 Python 一樣易於使用的編程語言，但具有 C++ 和 Rust 的性能。此外，Mojo 還提供了利用整個 Python 庫生態系統的能力。
Mojo 通過利用具有集成緩存、多線程和雲分發技術的下一代編譯器技術來實現這一壯舉。此外，Mojo 的自動調整和編譯時元編程功能允許您編寫可移植到最奇特硬件的代碼。
更重要的是，Mojo 允許您利用整個 Python 生態系統，以便您可以繼續使用您熟悉的工具。Mojo 旨在通過保留 Python 的動態功能同時添加新的系統編程原語，隨著時間的推移成為 Python 的超集。
這些新的系統編程原語將允許 Mojo 開發人員構建目前需要 C、C++、Rust、CUDA 和其他加速器系統的高性能庫。通過匯集最好的動態語言和系統語言，我們希望提供一個統一的跨抽象級別工作的編程模型對新手程序員很友好，並且可以擴展到從加速器到應用程序編程和腳本編寫的許多用例。

## #mojo的運行
使用 Mojo 編譯器
您可以從終端運行 Mojo 程序，就像使用 Python 一樣。因此，如果您有一個名為hello.mojo（或hello.🔥- 是的，文件擴展名可以是表情符號！）的文件，只需鍵入mojo hello.mojo：

```cmd
$ cat hello.🔥
def main():
    print("hello world")
    for x in range(9, 0, -3):
        print(x)
$ mojo hello.🔥
hello world
9
6
3
$
```

## #var&let
考慮到我們的兼容性目標以及 Python 在高級應用程序和動態 API 方面的優勢，我們不必花費太多時間來解釋該語言的這些部分是如何工作的。另一方面，Python 對系統編程的支持主要委託給 C，我們希望提供一個在該領域非常出色的單一系統。因此，本節詳細介紹了每個主要組件和功能，並通過示例描述瞭如何使用它們。

let和var聲明
在 Mojo 中的a 內部def，您可以為名稱分配一個值，它會隱式創建一個函數作用域變量，就像在 Python 中一樣。這提供了一種非常動態且簡單的代碼編寫方式，但它是一個挑戰，原因有二：

系統程序員通常希望聲明一個值是不可變的，以保證類型安全和性能。
如果他們在賦值中輸錯了變量名，他們可能希望得到一個錯誤。
為了支持這一點，Mojo 提供了作用域運行時值聲明：let是不可變的，並且var是可變的。這些值使用詞法作用域並支持名稱遮蔽：

def your_function(a, b):
    let c = a
    # Uncomment to see an error:
    # c = b  # error: c is immutable

    if c != b:
        let d = b
        print(d)

your_function(2, 3)

3
let和var聲明支持類型說明符和模式以及後期初始化：

def your_function():
    let x: Int = 42
    let y: Float64 = 17.0

    let z: Float32
    if x != 0:
        z = 1.0
    else:
        z = foo()
    print(z)

def foo() -> Float32:
    return 3.14

your_function()

1.0
請注意，在聲明中let和var是完全選擇加入的def。您仍然可以像使用 Python 一樣使用隱式聲明的值，並且它們照常獲得函數作用域。

## #註解方式
```mojo
# 這是一個單行註解

"""
這是一個
多行註解
"""
```

## #型別
### #Int與int的差別
在 Mojo 中，您可能會注意到我們使用Int（大寫“I”），這與 Python int（小寫“i”）不同。這種差異是故意的，而且實際上是一件好事！
在 Python 中，該int類型可以處理非常大的數字，並且具有一些額外的功能，例如檢查兩個數字是否是同一個對象。但這帶來了一些額外的負擔，可能會減慢速度。Mojo的則Int不同。它的設計簡單、快速，並針對您的計算機硬件進行了調整，以便快速處理。
我們做出這樣的選擇有兩個主要原因：
我們希望為需要與計算機硬件密切合作的程序員（系統程序員）提供一種透明且可靠的與硬件交互的方式。我們不想依靠花哨的技巧（比如 JIT 編譯器）來讓事情變得更快。
我們希望 Mojo 能夠與 Python 很好地配合，而不會引起任何問題。通過使用不同的名稱（Int 而不是 int），我們可以在 Mojo 中保留這兩種類型，而無需更改 Python int 的工作方式。
作為獎勵，Int遵循與您可能在 Mojo 中創建的其他自定義數據類型相同的命名風格。此外，Int它struct包含在 Mojo 的標準工具集中。
強類型檢查
儘管您仍然可以像在 Python 中一樣使用靈活的類型，但 Mojo 允許您使用嚴格的類型檢查。類型檢查可以使您的代碼更可預測、更易於管理且更安全。
使用強類型檢查的主要方法之一是使用 Mojo 的struct類型。Mojo 中的定義struct定義了一個編譯時綁定的名稱，並且在類型上下文中對該名稱的引用被視為所定義值的強規範。例如，考慮以下使用MyPair上面所示結構的代碼：
def pair_test() -> Bool:
    let p = MyPair(1, 2)
    # Uncomment to see an error:
    # return p < 4 # gives a compile time error
    return True

如果取消註釋第一個 return 語句並運行它，您將收到一個編譯時錯誤，告訴您無法4轉換為MyPair，這是 的 右側所__lt__()需要的（在MyPair定義中）。
在使用系統編程語言時，這是一種熟悉的體驗，但 Python 並不是這樣工作的。Python 對於MyPy類型註釋具有語法相同的功能，但它們不是由編譯器強制執行的：相反，它們是通知靜態分析的提示。通過將類型綁定到特定聲明，Mojo 可以處理經典類型註釋提示和強類型規範，而不會破壞兼容性。
類型檢查並不是強類型的唯一用例。由於我們知道類型是準確的，因此我們可以根據這些類型優化代碼，在寄存器中傳遞值，並在參數傳遞和其他低級細節方面與 C 一樣高效。這是 Mojo 為系統程序員提供安全性和可預測性保證的基礎。

##
##
##
##
##
##
##
##
##
##
##
##
##
##

## #函式
重載的函數和方法
與 Python 一樣，您可以在 Mojo 中定義函數而無需指定參數數據類型，Mojo 將動態處理它們。當您想要富有表現力的 API 只通過接受任意輸入並讓動態調度決定如何處理數據時，這很好。然而，當您想要確保類型安全時，如上所述，Mojo 還提供對重載函數和方法的全面支持。
這允許您定義多個具有相同名稱但具有不同參數的函數。這是許多語言（例如 C++、Java 和 Swift）中的常見功能。
解析函數調用時，Mojo 會嘗試每個候選者並使用有效的一個（如果只有一個有效），或者選擇最接近的匹配（如果它可以確定接近的匹配），或者如果它無法確定選擇哪一個，則報告該調用不明確。在後一種情況下，您可以通過在調用站點上添加顯式轉換來解決歧義。
讓我們看一個例子：
```mojo
struct Complex:
    var re: Float32
    var im: Float32

    fn __init__(inout self, x: Float32):
        """Construct a complex number given a real number."""
        self.re = x
        self.im = 0.0

    fn __init__(inout self, r: Float32, i: Float32):
        """Construct a complex number given its real and imaginary components."""
        self.re = r
        self.im = i
```
您可以重載結構和類中的方法以及重載模塊級函數。
Mojo 不支持僅在結果類型上重載，並且不使用結果類型或上下文類型信息進行類型推斷，從而使事情保持簡單、快速和可預測。Mojo 永遠不會產生“表達式太複雜”錯誤，因為它的類型檢查器根據定義是簡單且快速的。
同樣，如果您的參數名稱不帶類型定義，則該函數的行為就像具有動態類型的 Python 一樣。一旦定義了單個參數類型，Mojo 將查找重載候選者並解析函數調用，如上所述。
雖然我們還沒有討論參數（它們與函數參數不同），但您也可以基於參數重載函數和方法。
fn定義
上述擴展是提供低級編程和抽像功能的基石，但許多系統程序員更喜歡比defMojo 提供的更多控制和可預測性。回顧一下，def它的定義必須非常動態、靈活並且通常與 Python 兼容：參數是可變的，局部變量在第一次使用時隱式聲明，並且不強制執行作用域。這對於高級編程和腳本編寫來說非常有用，但對於系統編程來說並不總是那麼好。為了補充這一點，Mojo 提供了一個fn類似於def.
fn替代方案：我們可以添加修飾符或裝飾器，而不是使用像 這樣的新關鍵字@strict def。然而，無論如何我們都需要採用新的關鍵詞，而且這樣做的成本很低。此外，在系統編程領域的實踐中，fn它一直被使用，因此使其成為一流可能是有意義的。
就調用者而言，fn和def是可以互換的：沒有什麼是def可以提供而fn不能提供的（反之亦然）。不同之處在於，在其內部fn受到更多限制和控制（或者：迂腐和嚴格）。具體來說與def相比fn有許多限制
參數值默認在函數體內是不可變的（如 let），而不是可變的（如 var）。這會捕獲意外突變，並允許使用不可複制的類型作為參數。
參數值需要類型規範（self方法中除外），以捕獲類型規範的意外遺漏。同樣，缺少返回類型說明符會被解釋為返回None而不是未知的返回類型。請注意，兩者都可以顯式聲明為 return ，這允許人們根據需要object選擇加入的行為。def
局部變量的隱式聲明被禁用，因此必須聲明所有局部變量。let這可以捕獲名稱拼寫錯誤並與和提供的範圍相吻合var。
兩者都支持引發異常，但必須使用關鍵字顯式fn聲明raises。
不同團隊的編程模式會有很大差異，這種嚴格程度並不適合所有人。我們希望習慣 C++ 並已在 Python 中使用 MyPy 風格類型註釋的人們更喜歡使用fns，但更高級別的程序員和 ML 研究人員將繼續使用def. Mojo 允許您自由地混合def和fn聲明，例如用一種方法實現某些方法，用另一種方​​法實現另一些方法，並允許每個團隊或程序員決定什麼最適合他們的用例。
有關 Mojo 函數中參數行為的更多信息，請參閱下面有關參數傳遞控制和內存所有權的部分。
方法__copyinit__及__moveinit__特殊方法
Mojo 支持完整的“值語義”，如 C++ 和 Swift 等語言中所示，並且它使得使用裝飾器定義簡單的字段聚合變得非常@value容易。
對於高級用例，Mojo 允許您定義自定義構造函數（使用 Python 現有的__init__特殊方法）、自定義析構函數（使用現有的特殊方法）以及使用新的特殊方法的__del__自定義復制和移動構造函數。__copyinit____moveinit__
這些低級定制掛鉤在進行低級系統編程（例如手動內存管理）時非常有用。例如，考慮一個動態字符串類型，它需要在構造時為字符串數據分配內存，並在銷毀值時銷毀它：
```mojo
from Pointer import Pointer
from IO import print_no_newline

struct HeapArray:
    var data: Pointer[Int]
    var size: Int
    var cap: Int

    fn __init__(inout self):
        self.cap = 16
        self.size = 0
        self.data = Pointer[Int].alloc(self.cap)

    fn __init__(inout self, size: Int, val: Int):
        self.cap = size * 2
        self.size = size
        self.data = Pointer[Int].alloc(self.cap)
        for i in range(self.size):
            self.data.store(i, val)

    fn __del__(owned self):
        self.data.free()

    fn dump(self):
        print_no_newline("[")
        for i in range(self.size):
            if i > 0:
                print_no_newline(", ")
            print_no_newline(self.data.load(i))
        print("]")
```
該數組類型是使用低級函數實現的，以展示其工作原理的簡單示例。HeapArray但是，如果您嘗試使用運算符複製 的實例=，您可能會感到驚訝：
```mojo
var a = HeapArray(3, 1)
a.dump()   # Should print [1, 1, 1]
# Uncomment to see an error:
# var b = a  # ERROR: Vector doesn't implement __copyinit__

var b = HeapArray(4, 2)
b.dump()   # Should print [2, 2, 2, 2]
a.dump()   # Should print [1, 1, 1]

"""
[1, 1, 1]
[2, 2, 2, 2]
[1, 1, 1]
"""
```
如果取消註釋要復製a到 的行b，您將看到 Mojo 不允許您複製我們的數組：HeapArray包含一個實例Pointer（相當於低級 C 指針），並且 Mojo 不知道它指向什麼類型的數據或如何復制它。更一般地說，某些類型（如原子序數）無法複製或移動，因為它們的地址提供了一個身份，就像類實例一樣。
在這種情況下，我們確實希望我們的數組是可複制的。為了實現這一點，我們必須實現__copyinit__特殊的方法，通常是這樣實現的：
```mojo
struct HeapArray:
    var data: Pointer[Int]
    var size: Int
    var cap: Int

    fn __init__(inout self):
        self.cap = 16
        self.size = 0
        self.data = Pointer[Int].alloc(self.cap)

    fn __init__(inout self, size: Int, val: Int):
        self.cap = size * 2
        self.size = size
        self.data = Pointer[Int].alloc(self.cap)
        for i in range(self.size):
            self.data.store(i, val)

    fn __copyinit__(inout self, other: Self):
        self.cap = other.cap
        self.size = other.size
        self.data = Pointer[Int].alloc(self.cap)
        for i in range(self.size):
            self.data.store(i, other.data.load(i))

    fn __del__(owned self):
        self.data.free()

    fn dump(self):
        print_no_newline("[")
        for i in range(self.size):
            if i > 0:
                print_no_newline(", ")
            print_no_newline(self.data.load(i))
        print("]")
```
通過此實現，我們上面的代碼可以正常工作，並且b = a副本會生成邏輯上不同的數組實例，並具有自己的生命週期和數據：
```mojo
var a = HeapArray(3, 1)
a.dump()   # Should print [1, 1, 1]
# This is no longer an error:
var b = a

b.dump()   # Should print [1, 1, 1]
a.dump()   # Should print [1, 1, 1]
"""
[1, 1, 1]
[1, 1, 1]
[1, 1, 1]
"""
```
Mojo 還支持__moveinit__允許 Rust 風格的移動（在生命週期結束時獲取值）和 C++ 風格的移動（其中值的內容被刪除但析構函數仍然運行）的方法，並允許定義自定義移動邏輯。有關更多詳細信息，請參閱下面的“價值生命週期”部分。

Mojo 提供對值的生命週期的完全控制，包括使類型可複制、僅移動和不可移動的能力。這比 Swift 和 Rust 等語言提供的控制能力更強，後者要求值至少是可移動的。如果您好奇如何在不創建副本的情況下existing傳遞到方法中，請查看下面有關借用參數的部分。__copyinit__


## #struct
Mojo 基於 MLIR 和 LLVM，提供了用於多種編程語言的尖端編譯器和代碼生成系統。這讓我們可以更好地控制數據組織、直接訪問數據字段以及其他提高性能的方法。現代系統編程語言的一個重要特徵是能夠在這些複雜的低級操作之上構建高級且安全的抽象，而不會造成任何性能損失。在 Mojo 中，這是由struct類型提供的。
Mojo 中的Astruct與 Python 類似class：它們都支持方法、字段、運算符重載、元編程裝飾器等。它們的區別如下：
Python 類是動態的：它們允許動態調度、猴子修補（或“swizzling”）以及在運行時動態綁定實例屬性。
Mojo 結構是靜態的：它們在編譯時綁定（不能在運行時添加方法）。結構允許您以靈活性換取性能，同時安全且易於使用。
這是結構體的簡單定義：
```mojo
struct MyPair:
    var first: Int
    var second: Int

    # We use 'fn' instead of 'def' here - we'll explain that soon
    fn __init__(inout self, first: Int, second: Int):
        self.first = first
        self.second = second

    fn __lt__(self, rhs: MyPair) -> Bool:
        return self.first < rhs.first or
              (self.first == rhs.first and
               self.second < rhs.second)
```

從語法上講與Python的class相比的最大區別是struct中的所有實例屬性**必須**使用var或聲明顯式let聲明。
在Mojo中，“結構”的結構和內容是預先設置的，並且在程序運行時不能更改。與 Python 不同的是，在 Python 中您可以動態添加、刪除或更改對象的屬性，而 Mojo 不允許對結構進行這種操作。這意味著您不能del在程序運行過程中刪除方法或更改其值。
然而，靜態特性struct有一些很大的好處！它可以幫助 Mojo 更快地運行您的代碼。程序確切地知道在哪裡可以找到結構體的信息以及如何使用它，而無需任何額外的步驟或延遲。
Mojo 的結構也可以很好地與您可能已經從 Python 中了解的功能配合使用，例如運算符重載（它可以讓您更改數學符號對您自己的數據的喜愛+和使用方式）。-此外，所有“標準類型”（例如Int、Bool、String甚至Tuple）都是使用結構體創建的。這意味著它們是您可以使用的標準工具集的一部分，而不是硬連接到語言本身中。這為您在編寫代碼時提供了更大的靈活性和控制力。
如果您想知道參數inout的含義self：這表明參數是可變的，並且函數內部所做的更改對調用者可見。有關詳細信息，請參閱下面有關inout Arguments 的內容。


## 註解及參見

[簡寫一覽](abbreviationslist.md)






參數傳遞控制和內存所有權
在 Python 和 Mojo 中，大部分語言都圍繞函數調用：許多（顯然）內置行為是在標準庫中使用“dunder”（雙下劃線）方法實現的。在這些神奇的函數內部，許多內存所有權是通過參數傳遞來確定的。
讓我們回顧一下有關 Python 和 Mojo 如何傳遞參數的一些細節：
傳遞到Python def函數的所有值都使用引用語義。這意味著該函數可以修改傳遞給它的可變對象，並且這些更改在函數外部可見。然而，這種行為有時會讓外行人感到驚訝，因為您可以更改參數指向的對象，並且該更改在函數外部不可見。
默認情況下，傳遞到Mojo def函數的所有值都使用值語義。與 Python 相比，這是一個重要的區別：Mojodef函數接收所有參數的副本 - 它可以修改函數內部的參數，但更改在函數外部不可見。
默認情況下，傳遞到 Mojofn函數的所有值都是不可變引用。這意味著該函數可以讀取原始對象（它不是副本），但它根本無法修改該對象。
這種在 Mojo 中傳遞不可變參數的約定fn稱為“借用”。在以下部分中，我們將解釋如何更改 Mojo 中def和fn函數的參數傳遞行為。
為什麼論證約定很重要
在 Python 中，所有基本值都是對對象的引用 - 如上所述，Python 函數可以修改原始對象。因此，Python 開發人員習慣於將一切都視為參考語義。然而，在 CPython 或機器級別，您可以看到引用本身實際上是通過複製傳遞的- Python 複製指針並調整引用計數。
這種 Python 方法為大多數人提供了一個舒適的編程模型，但它要求所有值都進行堆分配（由於引用共享，結果有時會令人驚訝）。Mojo 類（TODO：將）對大多數對象遵循相同的引用語義方法，但這對於系統編程上下文中的整數等簡單類型來說並不實用。在這些場景中，我們希望這些值存在於堆棧中，甚至存在於硬件寄存器中。因此，Mojo 結構總是內聯到其容器中，無論是作為另一種類型的字段還是包含函數的堆棧幀。
這提出了一些有趣的問題：如何實現需要改變self結構類型的方法，例如__iadd__？它是如何let工作的以及如何防止突變？如何控制這些值的生命週期以使 Mojo 成為內存安全的語言？
答案是，Mojo 編譯器使用數據流分析和類型註釋來提供對值副本、引用別名和突變控制的完全控制。這些功能在很多方面與 Rust 語言中的功能相似，但它們的工作方式有所不同，以便使 Mojo 更容易學習，並且它們可以更好地集成到 Python 生態系統中，而不需要大量的註釋負擔。
在以下部分中，您將了解如何控制傳遞到 Mojofn函數的對象的內存所有權。
不可變參數 ( borrowed)
借用對像是對函數接收的對象的不可變引用，而不是接收該對象的副本。因此，被調用函數具有對該對象的完全讀取和執行訪問權限，但無法修改它（調用者仍然擁有該對象的獨占“所有權”）。
例如，考慮這個結構，我們在傳遞它的實例時不想複製它：
```mojo
# Don't worry about this code yet. It's just needed for the function below.
# It's a type so expensive to copy around so it does not have a
# __copyinit__ method.
struct SomethingBig:
    var id_number: Int
    var huge: HeapArray
    fn __init__(inout self, id: Int):
        self.huge = HeapArray(1000, 0)
        self.id_number = id

    # self is passed by-reference for mutation as described above.
    fn set_id(inout self, number: Int):
        self.id_number = number

    # Arguments like self are passed as borrowed by default.
    fn print_id(self):  # Same as: fn print_id(borrowed self):
        print(self.id_number)
```
當將 的實例傳遞SomethingBig給函數時，有必要傳遞引用，因為SomethingBig無法複製（它沒有__copyinit__方法）。並且，如上所述，fn默認情況下參數是不可變引用，但您可以使用borrowed關鍵字顯式定義它，如此處函數所示use_something_big()：
```mojo
fn use_something_big(borrowed a: SomethingBig, b: SomethingBig):
    """'a' and 'b' are both immutable, because 'borrowed' is the default."""
    a.print_id()
    b.print_id()

let a = SomethingBig(10)
let b = SomethingBig(20)
use_something_big(a, b)

""" =>
10
20
"""
```
此默認值統一適用於所有參數，包括self方法的參數。當傳遞大值或傳遞昂貴的值（如引用計數指針）（這是 Python/Mojo 類的默認值）時，這會更有效，因為傳遞參數時不必調用複制構造函數和析構函數。
因為函數的默認參數約定fn是borrowed，所以 Mojo 具有簡單且符合邏輯的代碼，默認情況下可以執行正確的操作。例如，我們不想僅僅SomethingBig為了調用print_id()方法或調用use_something_big().
這種借用參數約定在某些方麵類似於 C++ 中的參數傳遞const&，這避免了值的副本並禁用被調用者中的可變性。然而，借用的約定const&在兩個重要方面與 C++ 有所不同：
Mojo 編譯器實現了一個借用檢查器（類似於 Rust），該檢查器可以防止代碼在存在未完成的不可變引用時動態形成對某個值的可變引用，並且它可以防止對同一值進行多個可變引用。您可以進行多次借用（如use_something_big上面的調用所示），但不能通過可變引用傳遞某些內容並同時藉用。（TODO：當前未啟用）。
Int像、Float、 和 這樣的小值SIMD直接在機器寄存器中傳遞，而不是通過額外的間接傳遞（這是因為它們是用裝飾@register_passable器聲明的）。與 C++ 和 Rust 等語言相比，這是一個顯著的性能增強，並將這種優化從每個調用站點轉移到對類型進行聲明。
與 Rust 類似，Mojo 的借用檢查器強制執行不變量的排他性。Rust 和 Mojo 之間的主要區別在於，Mojo 不需要調用方有一個印記來傳遞借用。此外，Mojo 在傳遞小值時效率更高，而 Rust 默認移動值而不是通過借用傳遞它們。這些策略和語法決策使 Mojo 能夠提供更易於使用的編程模型。
可變參數 ( inout)
另一方面，如果您定義一個fn函數並希望參數可變，則必須使用關鍵字將參數聲明為可變的inout。
提示：當您看到 時inout，這意味著對函數內部參數所做的任何更改在函數外部都是可見的。
考慮以下示例，其中__iadd__函數（實現就地添加操作，例如x += 2）嘗試修改self：
```mojo
struct MyInt:
    var value: Int
    fn __init__(inout self, v: Int):
        self.value = v

    fn __copyinit__(inout self, other: MyInt):
        self.value = other.value

    # self and rhs are both immutable in __add__.
    fn __add__(self, rhs: MyInt) -> MyInt:
        return MyInt(self.value + rhs.value)

    # ... but this cannot work for __iadd__
    # Uncomment to see the error:
    #fn __iadd__(self, rhs: Int):
    #    self = self + rhs  # ERROR: cannot assign to self!
```

如果取消註釋該__iadd__()方法，您將收到編譯器錯誤。

這裡的問題是 是self不可變的，因為這是一個 Mojofn函數，所以它不能改變參數的內部狀態（默認參數約定是borrowed）。inout解決方案是通過在參數名稱上添加關鍵字來聲明參數是可變的self：

```mojo
struct MyInt:
    var value: Int

    fn __init__(inout self, v: Int):
        self.value = v

    fn __copyinit__(inout self, other: MyInt):
        self.value = other.value

    # self and rhs are both immutable in __add__.
    fn __add__(self, rhs: MyInt) -> MyInt:
        return MyInt(self.value + rhs.value)

    # ... now this works:
    fn __iadd__(inout self, rhs: Int):
        self = self + rhs
```

現在self參數在函數中是可變的，並且任何更改在調用者中都是可見的，因此我們可以使用以下命令執行就地加法MyInt：
```mojo
var x: MyInt = 42
x += 1
print(x.value) # prints 43 as expected

# However...
let y = x
# Uncomment to see the error:
# y += 1       # ERROR: Cannot mutate 'let' value


# => 43
```

如果取消註釋上面的最後一行，則let值的突變會失敗，因為不可能形成對不可變值的可變引用（let使變量不可變）。

當然，您可以聲明多個inout參數。例如，您可以像這樣定義和使用交換函數：
```mojo
fn swap(inout lhs: Int, inout rhs: Int):
    let tmp = lhs
    lhs = rhs
    rhs = tmp

var x = 42
var y = 12
print(x, y)  # Prints 42, 12
swap(x, y)
print(x, y)  # Prints 12, 42
"""=>
42 12
12 42
"""
```
該系統的一個非常重要的方面是它的所有組成都是正確的。

請注意，我們不將此參數稱為“通過引用”傳遞。儘管inout約定在概念上是相同的，但我們不將其稱為按引用傳遞，因為實現實際上可能使用指針傳遞值。

傳遞參數 (owned和^)
Mojo 支持的最後一個參數約定是owned參數約定。此約定用於想要獲得值的獨占所有權的函數，並且通常與後綴運算^符一起使用。

例如，假設您正在使用僅移動類型，例如唯一指針：
```mojo
# This is not really a unique pointer, we just model its behavior here
# to serve the examples below.
struct UniquePointer:
    var ptr: Int

    fn __init__(inout self, ptr: Int):
        self.ptr = ptr

    fn __moveinit__(inout self, owned existing: Self):
        self.ptr = existing.ptr

    fn __del__(owned self):
        self.ptr = 0
```

雖然該borrow約定使得無需儀式即可輕鬆使用這個獨特的指針，但在某些時候您可能希望將所有權轉移給某些其他函數。在這種情況下，您需要^對活字印刷術使用“傳輸”操作符。

運算^符結束值綁定的生命週期，並將值所有權轉移給其他東西（在下面的示例中，所有權轉移給函數take_ptr()）。為了支持這一點，您可以將函數定義為接受owned參數。例如，您可以定義take_ptr()獲取參數的所有權，如下所示：

fn take_ptr(owned p: UniquePointer):
    print("take_ptr")
    print(p.ptr)

fn use_ptr(borrowed p: UniquePointer):
    print("use_ptr")
    print(p.ptr)

fn work_with_unique_ptrs():
    let p = UniquePointer(100)
    use_ptr(p)    # Pass to borrowing function.
    take_ptr(p^)  # Pass ownership of the `p` value to another function.

    # Uncomment to see an error:
    # use_ptr(p) # ERROR: p is no longer valid here!

work_with_unique_ptrs()

use_ptr
100
take_ptr
100
請注意，如果取消對第二次調用的註釋use_ptr()，則會收到錯誤，因為該p值已傳輸到該take_ptr()函數，因此該p值被銷毀。

因為它已被聲明owned，所以該take_ptr()函數知道它具有對該值的唯一訪問權。這對於諸如唯一指針之類的事情非常重要，並且當您想要避免複製時它很有用。

例如，您將特別看到owned關於析構函數和消耗移動初始值設定項的約定。例如，我們之前定義的結構體在其方法中HeapArray使用，因為您需要擁有一個值才能銷毀它（或者在移動構造函數的情況下竊取其部分）。owned__del__()

比較def和fn參數傳遞
Mojo 的def函數本質上只是為fn函數加糖：

沒有顯式類型註釋的參數def默認為Object.

def沒有約定關鍵字（例如inoutor ）的參數owned通過隱式複制傳遞到與參數同名的可變變量中。（這要求該類型有一個__copyinit__方法。）

例如，這兩個函數具有相同的行為：

def example(inout a: Int, b: Int, c):
    # b and c use value semantics so they're mutable in the function
    ...

fn example(inout a: Int, b_in: Int, c_in: Object):
    # b_in and c_in are immutable references, so we make mutable shadow copies
    var b = b_in
    var c = c_in
    ...

卷影副本通常不會增加開銷，因為像這樣的小類型的引用Object複制起來很便宜。昂貴的部分是調整引用計數，但這可以通過移動優化來消除。

Python集成
在 Mojo 中使用您熟悉和喜愛的 Python 模塊非常簡單。您可以將任何 Python 模塊導入到 Mojo 程序中，並從 Mojo 類型創建 Python 類型。

導入Python模塊
要在 Mojo 中導入 Python 模塊，只需Python.import_module()使用模塊名稱進行調用：

from PythonInterface import Python

# This is equivalent to Python's `import numpy as np`
let np = Python.import_module("numpy")

# Now use numpy as if writing in Python
array = np.array([1, 2, 3])
print(array)

[1 2 3]
是的，這會導入 Python NumPy，並且您可以導入任何其他 Python 模塊。

目前，您無法導入單個成員（例如單個 Python 類或函數），您必須導入整個 Python 模塊，然後通過模塊名稱訪問成員。

Python 中的 Mojo 類型
Mojo 原始類型隱式轉換為 Python 對象。今天，我們支持列表、元組、整數、浮點數、布爾值和字符串。

例如，給定這個打印 Python 類型的 Python 函數：

%%python
def type_printer(my_list, my_tuple, my_int, my_string, my_float):
    print(type(my_list))
    print(type(my_tuple))
    print(type(my_int))
    print(type(my_string))
    print(type(my_float))

您可以毫無問題地傳遞 Python 函數 Mojo 類型：

type_printer([0, 3], (False, True), 4, "orange", 3.4)

<class 'list'>
<class 'tuple'>
<class 'int'>
<class 'str'>
<class 'float'>
請注意，在 Jupyter 筆記本中，上面聲明的 Python 函數可自動供以下代碼單元中的任何 Mojo 代碼使用。

Mojo 還沒有標準字典，因此還無法從 Mojo 字典創建 Python 字典。不過，您可以在 Mojo 中使用 Python 字典！要創建 Python 字典，請使用以下dict方法：

from PythonInterface import Python
from PythonObject import PythonObject
from IO import print
from Range import range

var dictionary = Python.dict()
dictionary["fruit"] = "apple"
dictionary["starch"] = "potato"

var keys: PythonObject = ["fruit", "starch", "protein"]
var N: Int = keys.__len__().__index__()
print(N, "items")

for i in range(N):
    if Python.is_type(dictionary.get(keys[i]), Python.none()):
        print(keys[i], "is not in dictionary")
    else:
        print(keys[i], "is included")

3 items
fruit is included
starch is included
protein is not in dictionary
導入本地Python模塊
如果您想在 Mojo 中使用一些本地 Python 代碼，只需將目錄添加到 Python 路徑，然後導入模塊即可。

例如，假設您有一個名為的 Python 文件mypython.py：

import numpy as np

def my_algorithm(a, b):
    array_a = np.random.rand(a, a)
    return array_a + b

以下是導入它並在 Mojo 文件中使用它的方法：

from PythonInterface import Python

Python.add_to_path("path/to/module")
let mypython = Python.import_module("mypython")

let c = mypython.my_algorithm(2, 3)
print(c)

在 Mojo 中使用 Python 時無需擔心內存管理問題。一切都正常，因為 Mojo 從一開始就是為 Python 設計的。

參數化：編譯時元編程
Python 最令人驚奇的功能之一是其可擴展的運行時元編程功能。這使得廣泛的庫成為可能，並提供了靈活且可擴展的編程模型，世界各地的 Python 程序員都可以從中受益。不幸的是，這些功能也是有代價的：因為它們是在運行時評估的，所以它們直接影響底層代碼的運行時效率。由於 IDE 不知道它們，因此代碼完成等 IDE 功能很難理解它們並使用它們來改善開發人員體驗。

在Python生態系統之外，靜態元編程也是開發的重要組成部分，可以開發新的編程範例和高級庫。這個領域有許多現有技術的例子，具有不同的權衡，例如：

預處理器（例如C 預處理器、Lex/YACC 等）可能是最繁重的。它們完全通用，但在開發人員體驗和工具集成方面最差。

一些語言（如 Lisp 和 Rust）支持（有時是“衛生的”）宏擴展功能，通過更好的工具集成實現語法擴展和样板文件減少。

一些較舊的語言（例如 C++）具有非常龐大且複雜的元編程語言（模板），它們是運行時語言的雙重語言。這些尤其難以學習，並且編譯時間和錯誤消息都很差。

有些語言（如 Swift）以一流的方式將許多功能構建到核心語言中，為常見情況提供良好的人體工程學效果，但犧牲了通用性。

一些較新的語言（例如 Zig）將語言解釋器集成到編譯流程中，並允許解釋器在編譯 AST 時進行反映。這使得許多與宏系統相同的功能具有更好的擴展性和通用性。

對於 Modular 在人工智能、高性能機器學習內核和加速器方面的工作，我們需要先進的元編程系統提供的高抽象能力。我們需要高級的零成本抽象、富有表現力的庫以及多種算法變體的大規模集成。我們希望庫開發人員能夠擴展系統，就像他們在 Python 中所做的那樣，提供一個可擴展的開發平台。

也就是說，我們不願意犧牲開發人員體驗（​​包括編譯時間和錯誤消息），也沒有興趣構建難以教授的並行語言生態系統。我們可以向這些以前的系統學習，但也可以在其基礎上構建新技術，包括 MLIR 和細粒度語言集成緩存技術。

因此，Mojo 支持編譯器中內置的編譯時元編程，作為編譯的一個單獨階段——在解析、語義分析和 IR 生成之後，但在降低到特定於目標的代碼之前。它對運行時程序使用與元程序相同的宿主語言，並利用 MLIR 以可預測的方式表示和評估這些程序。

讓我們看一些簡單的例子。

關於“參數”： Python 開發人員可以互換地使用“參數”和“參數”這兩個詞來表示“傳遞到函數中的東西”。我們決定回收“參數”和“參數表達式”來表示 Mojo 中的編譯時值，並繼續使用“參數”和“表達式”來引用運行時值。這使我們能夠圍繞“參數化”和“參數化”等詞進行對齊，以進行編譯時元編程。

定義參數化類型和函數
您可以通過在方括號中指定參數名稱和類型來參數化結構和函數（使用PEP695 語法的擴展版本）。與參數值不同，參數值在編譯時是已知的，這可以實現額外級別的抽象和代碼重用，以及自動調整等編譯器優化。

例如，讓我們看一下SIMD類型，它表示硬件中保存標量數據類型的多個實例的低級向量寄存器。硬件加速器不斷引入新的向量數據類型，甚至CPU也可能有512位或更長的SIMD向量。為了訪問這些處理器上的 SIMD 指令，必須將數據整形為正確的 SIMD 寬度（數據類型）和長度（向量大小）。

然而，用 Mojo 的內置類型定義所有不同的 SIMD 變體是不可行的。因此，Mojo 的SIMD類型（定義為結構）在其方法中公開了常見的 SIMD 操作，並使 SIMD 數據類型和大小值參數化。這使您可以將數據直接映射到任何硬件上的 SIMD 向量。

這是 Mojo 類型定義的精簡（非功能）版本SIMD：

struct SIMD[type: DType, size: Int]:
    var value: … # Some low-level MLIR stuff here

    # Create a new SIMD from a number of scalars
    fn __init__(inout self, *elems: SIMD[type, 1]):  ...

    # Fill a SIMD with a duplicated scalar value.
    @staticmethod
    fn splat(x: SIMD[type, 1]) -> SIMD[type, size]: ...

    # Cast the elements of the SIMD to a different elt type.
    fn cast[target: DType](self) -> SIMD[target, size]: ...

    # Many standard operators are supported.
    fn __add__(self, rhs: Self) -> Self: ...

使用參數定義每個 SIMD 變體非常有利於代碼重用，因為該SIMD類型可以靜態地表達所有不同的向量變體，而不需要語言預先定義每個變體。

因為SIMD是參數化類型，所以self其函數中的實參攜帶這些參數——完整的類型名稱是SIMD[type, size]。儘管將其寫出是有效的（如 的返回類型所示splat()），但這可能會很冗長，因此我們建議像示例一樣使用該Self類型（來自PEP673）__add__。

參數重載
函數和方法可以在其參數簽名上重載。重載決策邏輯根據以下規則（按優先順序）過濾候選者：

具有最少數量隱式轉換（在實參和參數中）的候選者。
沒有可變參數的候選人。
沒有可變參數的候選者。
具有最短參數簽名的候選者。
如果應用這些規則後存在多個候選者，則重載決策將失敗。例如：

@register_passable("trivial")
struct MyInt:
    """A type that is implicitly convertible to `Int`."""
    var value: Int

    @always_inline("nodebug")
    fn __init__(_a: Int) -> Self:
        return Self {value: _a}

fn foo[x: MyInt, a: Int]():
  print("foo[x: MyInt, a: Int]()")

fn foo[x: MyInt, y: MyInt]():
  print("foo[x: MyInt, y: MyInt]()")

fn bar[a: Int](b: Int):
  print("bar[a: Int](b: Int)")

fn bar[a: Int](*b: Int):
  print("bar[a: Int](*b: Int)")

fn bar[*a: Int](b: Int):
  print("bar[*a: Int](b: Int)")

fn parameter_overloads[a: Int, b: Int, x: MyInt]():
    # `foo[x: MyInt, a: Int]()` is called because it requires no implicit
    # conversions, whereas `foo[x: MyInt, y: MyInt]()` requires one.
    foo[x, a]()

    # `bar[a: Int](b: Int)` is called because it does not have variadic
    # arguments or parameters.
    bar[a](b)

    # `bar[*a: Int](b: Int)` is called because it has variadic parameters.
    bar[a, a, a](b)

parameter_overloads[1, 2, MyInt(3)]()

foo[x: MyInt, a: Int]()
bar[a: Int](b: Int)
bar[*a: Int](b: Int)
使用參數化類型和函數
您可以通過將值傳遞給方括號中的參數來實例化參數類型和函數。例如，對於SIMD上面的類型，type指定數據類型並size指定SIMD向量的長度（必須是2的冪）：

from DType import DType
from SIMD import SIMD

# Make a vector of 4 floats.
let small_vec = SIMD[DType.float32, 4](1.0, 2.0, 3.0, 4.0)

# Make a big vector containing 1.0 in float16 format.
let big_vec = SIMD[DType.float16, 32].splat(1.0)

# Do some math and convert the elements to float32.
let bigger_vec = (big_vec+big_vec).cast[DType.float32]()

# You can write types out explicitly if you want of course.
let bigger_vec2 : SIMD[DType.float32, 32] = bigger_vec

print('small_vec type:', small_vec.element_type, 'length:', len(small_vec))
print('bigger_vec2 type:', bigger_vec2.element_type, 'length:', len(bigger_vec2))

small_vec type: float32 length: 4
bigger_vec2 type: float32 length: 32
請注意，該cast()方法還需要一個參數來指定您想要的類型轉換（上面的方法定義需要一個target參數值）。因此，就像SIMD結構是泛型類型定義一樣，cast()方法也是泛型方法定義，它根據參數值在編譯時而不是運行時實例化。

上面的代碼顯示了具體類型的使用（即，它SIMD使用已知類型值進行實例化），但參數的主要功能來自於定義參數算法和類型（使用參數值的代碼）的能力。例如，以下是如何定義與SIMD類型和寬度無關的參數算法：

from Math import sqrt

fn rsqrt[dt: DType, width: Int](x: SIMD[dt, width]) -> SIMD[dt, width]:
    return 1 / sqrt(x)

print(rsqrt[DType.float16, 4](42))

[0.154296875, 0.154296875, 0.154296875, 0.154296875]
請注意，x參數實際上是SIMD基於函數參數的類型。運行時程序可以使用參數的值，因為參數在運行時程序需要它們之前在編譯時解析（但編譯時參數表達式不能使用運行時值）。

Mojo 編譯器對於參數的類型推斷也很智能。請注意，上述函數無需sqrt()指定參數即可調用參數函數 - 編譯器會推斷其參數，就像您sqrt[type, simd_width](x)顯式編寫一樣。另請注意，rsqrt()選擇定義其第一個參數 name ，width即使SIMD類型將其命名為 it size，也沒有問題。

參數表達式只是 Mojo 代碼
a+b參數表達式是出現在需要參數的位置的任何代碼表達式（例如）。參數表達式支持運算符和函數調用，就像運行時代碼一樣，並且所有參數類型都使用與運行時程序相同的類型系統（例如Int和DType）。

由於參數表達式使用與運行時 Mojo 代碼相同的語法和類型，因此您可以使用許多“依賴類型”功能。例如，您可能想要定義一個輔助函數來連接兩個 SIMD 向量：

fn concat[ty: DType, len1: Int, len2: Int](
        lhs: SIMD[ty, len1], rhs: SIMD[ty, len2]) -> SIMD[ty, len1+len2]:

    var result = SIMD[ty, len1 + len2]()
    for i in range(len1):
        result[i] = SIMD[ty, 1](lhs[i])
    for j in range(len2):
        result[len1 + j] = SIMD[ty, 1](rhs[j])
    return result

let a = SIMD[DType.float32, 2](1, 2)
let x = concat[DType.float32, 2, 2](a, a)

print('result type:', x.element_type, 'length:', len(x))

result type: float32 length: 4
請注意，結果長度是輸入向量長度的總和，您可以通過簡單的+操作來表達它。對於更複雜的示例，請看一下SIMD.shuffle()標準庫中的方法：它接受兩個輸入 SIMD 值、一個向量洗牌掩碼作為列表，並返回一個與洗牌掩碼長度匹配的 SIMD。

強大的編譯時編程
雖然簡單的表達式很有用，但有時您希望使用控制流編寫命令式編譯時邏輯。例如，isclose()MojoMath模塊中的函數對整數使用精確相等，但對浮點使用“接近”比較。您甚至可以進行編譯時遞歸。例如，下面是一個示例“樹縮減”算法，它將向量的所有元素遞歸地求和為標量：

fn slice[ty: DType, new_size: Int, size: Int](
        x: SIMD[ty, size], offset: Int) -> SIMD[ty, new_size]:
    var result = SIMD[ty, new_size]()
    for i in range(new_size):
        result[i] = SIMD[ty, 1](x[i + offset])
    return result

fn reduce_add[ty: DType, size: Int](x: SIMD[ty, size]) -> Int:
    @parameter
    if size == 1:
        return x[0].to_int()
    elif size == 2:
        return x[0].to_int() + x[1].to_int()

    # Extract the top/bottom halves, add them, sum the elements.
    alias half_size = size // 2
    let lhs = slice[ty, half_size, size](x, 0)
    let rhs = slice[ty, half_size, size](x, half_size)
    return reduce_add[ty, half_size](lhs + rhs)
    
let x = SIMD[DType.index, 4](1, 2, 3, 4)
print(x)
print("Elements sum:", reduce_add[DType.index, 4](x))

[1, 2, 3, 4]
Elements sum: 10
這利用了該@parameter if功能，即if在編譯時運行的語句。它要求其條件是有效的參數表達式，並確保只有語句的實時分支if被編譯到程序中。

Mojo 類型只是參數表達式
雖然我們已經展示瞭如何在類型中使用參數表達式，但類型註釋本身可以是任意表達式（就像在 Python 中一樣）。Mojo 中的類型具有特殊的元類型，允許定義類型參數算法和函數。

例如，我們可以創建一個Array支持任意類型元素的簡化版本（通過AnyType參數）：

struct Array[T: AnyType]:
    var data: Pointer[T]
    var size: Int
    var cap: Int

    fn __init__(inout self, size: Int, value: T):
        self.cap = size * 2
        self.size = size
        self.data = Pointer[T].alloc(self.cap)
        for i in range(self.size):
            self.data.store(i, value)
              
    fn __getitem__(self, i: Int) -> T:
        return self.data.load(i)

    fn __del__(owned self):
        self.data.free()

var v = Array[Float32](4, 3.14)
print(v[0], v[1], v[2], v[3])

3.1400001049041748 3.1400001049041748 3.1400001049041748 3.1400001049041748
請注意，T參數被用作參數的形式類型value和函數的返回類型__getitem__。參數允許Array類型根據不同的用例提供不同的 API。

還有許多其他情況可以從參數的更高級使用中受益。例如，您可以並行執行閉包 N 次，並從上下文中輸入一個值，如下所示：

fn parallelize[func: fn (Int) -> None](num_work_items: Int):
    # Not actually parallel: see the 'Functional' module for real implementation.
    for i in range(num_work_items):
        func(i)

另一個重要的例子是可變參數泛型，其中可能需要在異構類型列表上定義算法或數據結構，例如元組：

struct Tuple[*Ts: AnyType]:
    var _storage : *Ts

儘管我們還沒有足夠的元類型助手，但我們將來應該能夠編寫類似的東西（儘管重載仍然是處理此問題的更好方法）：

struct Array[T: AnyType]:
    fn __getitem__[IndexType: AnyType](self, idx: IndexType)
       -> (ArraySlice[T] if issubclass(IndexType, Range) else T):
       ...

alias: 命名參數表達式
想要命名編譯時值是很常見的。雖然var定義了運行時值並let定義了運行時常量，但我們需要一種方法來定義編譯時臨時值。為此，Mojo 使用alias聲明。

例如，該DType結構使用枚舉器的別名實現一個簡單的枚舉，如下所示（實際DType實現細節略有不同）：

struct DType:
    var value : UI8
    alias invalid = DType(0)
    alias bool = DType(1)
    alias int8 = DType(2)
    alias uint8 = DType(3)
    alias int16 = DType(4)
    alias int16 = DType(5)
    ...
    alias float32 = DType(15)

這允許客戶端自然地用作DType.float32參數表達式（也可以用作運行時值）。DType請注意，這是在編譯時調用運行時構造函數。

類型是別名的另一個常見用途。因為類型是編譯時表達式，所以能夠很方便地執行以下操作：

alias Float16 = SIMD[DType.float16, 1]
alias UInt8 = SIMD[DType.uint8, 1]

var x : Float16   # F16 works like a "typedef"

與var和 一樣let，別名遵循範圍，並且您可以按照預期在函數中使用本地別名。

順便說一下， 和None都AnyType被定義為類型別名。

自動調整/自適應編譯
Mojo 參數表達式允許您像在其他語言中一樣編寫可移植的參數算法，但是在編寫高性能代碼時，您仍然必須選擇用於參數的具體值。例如，在編寫高性能數值算法時，您可能希望使用內存平鋪來加速算法，但要使用的維度在很大程度上取決於可用的硬件功能、緩存的大小、融合到內核中的內容以及許多其他繁瑣的細節。

即使向量長度也可能難以管理，因為典型機器的向量長度取決於數據類型，並且某些數據類型bfloat16並不完全支持所有實現。Mojo 通過autotune在標準庫中提供一個函數來提供幫助。例如，如果您想將與向量長度無關的算法寫入數據緩衝區，您可以這樣編寫：

from DType import DType
from Autotune import autotune, search
from Benchmark import Benchmark
from Pointer import DTypePointer
from Functional import vectorize

fn buffer_elementwise_add_impl[
    dt: DType
](lhs: DTypePointer[dt], rhs: DTypePointer[dt], result: DTypePointer[dt], N: Int):
    """Perform elementwise addition of N elements in RHS and LHS and store
    the result in RESULT.
    """
    @parameter
    fn add_simd[size: Int](idx: Int):
        let lhs_simd = lhs.simd_load[size](idx)
        let rhs_simd = rhs.simd_load[size](idx)
        result.simd_store[size](idx, lhs_simd + rhs_simd)
    
    # Pick vector length for this dtype and hardware
    alias vector_len = autotune(1, 4, 8, 16, 32)

    # Use it as the vectorization length
    vectorize[vector_len, add_simd](N)

fn elementwise_evaluator[dt: DType](
    fns: Pointer[fn (DTypePointer[dt], DTypePointer[dt], DTypePointer[dt], Int) -> None],
    num: Int,
) -> Int:
    # Benchmark the implementations on N = 64.
    alias N = 64
    let lhs = DTypePointer[dt].alloc(N)
    let rhs = DTypePointer[dt].alloc(N)
    let result = DTypePointer[dt].alloc(N)

    # Fill with ones.
    for i in range(N):
        lhs.store(i, 1)
        rhs.store(i, 1)

    # Find the fastest implementation.
    var best_idx: Int = -1
    var best_time: Int = -1
    for i in range(num):
        @parameter
        fn wrapper():
            fns.load(i)(lhs, rhs, result, N)
        let cur_time = Benchmark(1).run[wrapper]()
        if best_idx < 0 or best_time > cur_time:
            best_idx = i
            best_time = cur_time
        print("time[", i, "] =", cur_time)
    print("selected:", best_idx)
    return best_idx

fn buffer_elementwise_add[
    dt: DType
](lhs: DTypePointer[dt], rhs: DTypePointer[dt], result: DTypePointer[dt], N: Int):
    # Forward declare the result parameter.
    alias best_impl: fn(DTypePointer[dt], DTypePointer[dt], DTypePointer[dt], Int) -> None

    # Perform search!
    search[
      fn(DTypePointer[dt], DTypePointer[dt], DTypePointer[dt], Int) -> None,
      buffer_elementwise_add_impl[dt],
      elementwise_evaluator[dt] -> best_impl
    ]()

    # Call the select implementation
    best_impl(lhs, rhs, result, N)

我們現在可以像往常一樣調用我們的函數：

let N = 32
let a = DTypePointer[DType.float32].alloc(N)
let b = DTypePointer[DType.float32].alloc(N)
let res = DTypePointer[DType.float32].alloc(N)
# Initialize arrays with some values
for i in range(N):
    a.store(i, 2.0)
    b.store(i, 40.0)
    res.store(i, -1)
    
buffer_elementwise_add[DType.float32](a, b, res, N)
print(a.load(10), b.load(10), res.load(10))

time[ 0 ] = 24
time[ 1 ] = 6
time[ 2 ] = 4
time[ 3 ] = 4
time[ 4 ] = 4
selected: 2
2.0 40.0 42.0
編譯此代碼的實例時，Mojo 會分叉此算法的編譯，並通過測量在實踐中最適合目標硬件的值來決定使用哪個值。它評估表達式的不同值vector_len，並根據用戶定義的性能評估器選擇最快的值。例如，因為它單獨測量和評估每個選項，所以它可能會為 選取不同的向量長度float32。int8這個簡單的功能非常強大——超越了簡單的整數常量——因為函數和類型也是參數表達式。

請注意，最佳向量長度的搜索是由該search()函數執行的。search()接受一個評估器和一個分叉函數，並返回評估器選擇的最快實現作為參數結果。要更深入地了解此主題，請查看有關Mojo 中的矩陣乘法和Fast Memset的筆記本。

自動調優本質上是一種指數技術，受益於 Mojo 編譯器堆棧的內部實現細節（特別是 MLIR、集成緩存和編譯分發）。這也是一個高級用戶功能，需要隨著時間的推移不斷開發和迭代。

“價值生命週期”：價值的誕生、存在和消亡
此時，您應該了解 Mojo 函數和類型的核心語義和功能，因此我們現在可以討論它們如何組合在一起以在 Mojo 中表達新類型。

許多現有語言都通過不同的權衡來表達設計點：例如，C++ 非常強大，但經常被指責“默認設置錯誤”，從而導致錯誤和錯誤功能。Swift 易於使用，但其模型的可預測性較差，會復制大量值，並且依賴於“ARC 優化器”來提高性能。Rust 從強大的價值所有權目標開始，以滿足其借用檢查器的要求，但依賴於可移動的值，這使得表達自定義移動構造函數變得具有挑戰性，並且會給性能帶來很大的壓力memcpy。在Python中，一切都是對類的引用，因此它永遠不會真正面臨類型問題。

對於 Mojo，我們從這些現有系統中學習，我們的目標是提供一個非常強大且易於學習和理解的模型。我們也不想要求“盡最大努力”和難以預測的優化過程內置到“足夠智能”的編譯器中。

為了探索這些問題，我們研究了不同的價值分類和表達它們的相關 Mojo 功能，並自下而上構建。我們在示例中使用 C++ 作為主要比較點，因為它眾所周知，但如果其他語言提供了更好的比較點，我們偶爾會參考它們。

無法實例化的類型
Mojo 中最簡單的類型是不允許創建它的實例的類型：這些類型根本沒有初始化程序，如果它們有析構函數，則永遠不會調用它（因為無法銷毀實例）：

struct NoInstances:
    var state: Int  # Pretty useless

    alias my_int = Int

    @staticmethod
    fn print_hello():
        print("hello world")

默認情況下，Mojo 類型不會獲得默認構造函數、移動構造函數、成員初始化器或其他任何內容，因此不可能創建此NoInstances類型的實例。為了獲得它們，您需要定義一個__init__方法或使用合成初始化程序的裝飾器。如圖所示，這些類型可用作“命名空間”，因為您可以引用靜態成員，例如NoInstances.my_int或NoInstances.print_hello()即使您無法實例化該類型的實例。

不可移動和不可複制類型
如果我們在復雜性的階梯上更進一步，我們將得到可以實例化的類型，但是一旦它們被固定到內存中的地址，它們就不能被隱式移動或複制。這對於實現原子操作（例如std::atomic在 C++ 中）等類型或其他類型非常有用，其中值的內存地址是其標識並且對其用途至關重要：

struct Atomic:
    var state: Int

    fn __init__(inout self, state: Int = 0):
        self.state = state

    fn __iadd__(inout self, rhs: Int):
        #...atomic magic...

    fn get_value(self) -> Int:
        return atomic_load_int(self.state)

此類定義了一個初始化程序，但沒有復製或移動構造函數，因此一旦初始化，就永遠無法移動或複制。這是安全且有用的，因為 Mojo 的所有權系統是完全“地址正確的”——當它被初始化到堆棧或其他類型的字段中時，它永遠不需要移動。

請注意，Mojo 的方法僅控制內置移動操作，例如a = b復制和^傳輸運算符。您可以用於自己的類型（如上Atomic）的一種有用模式是添加顯式copy()方法（非“dunder”方法）。當程序員知道實例是安全的時，這對於製作實例的顯式副本很有用。

獨特的“僅移動”類型
如果我們在能力的階梯上再上一層樓，我們將遇到“唯一”的類型 - C++ 中有很多這樣的例子，例如類似的類型，甚至是擁有底層 POSIX 文件描述符的std::unique_ptr類型FileDescriptor。這些類型在 Rust 等語言中很普遍，不鼓勵複製，但“移動”是免費的。__moveinit__在 Mojo 中，您可以通過定義獲取唯一類型所有權的方法來實現這些類型的移動。例如：

# This is a simple wrapper around POSIX-style fcntl.h functions.
struct FileDescriptor:
    var fd: Int

    # This is how we move our unique type.
    fn __moveinit__(inout self, owned existing: Self):
        self.fd = existing.fd

    # This takes ownership of a POSIX file descriptor.
    fn __init__(inout self, fd: Int):
        self.fd = fd

    fn __init__(inout self, path: String):
        # Error handling omitted, call the open(2) syscall.
        self = FileDescriptor(open(path, ...))

    fn __del__(owned self):
        close(self.fd)   # pseudo code, call close(2)

    fn dup(self) -> Self:
        # Invoke the dup(2) system call.
        return Self(dup(self.fd))
    fn read(...): ...
    fn write(...): ...

消費移動構造函數 ( __moveinit__) 獲取現有 的所有權FileDescriptor，並將其內部實現細節移動到新實例。這是因為 的實例FileDescriptor可能存在於不同的位置，並且它們可以在邏輯上移動——竊取一個值的主體並將其移動到另一個值中。

這是一個會__moveinit__多次調用的令人震驚的示例：

fn egregious_moves(owned fd1: FileDescriptor):
    # fd1 and fd2 have different addresses in memory, but the
    # transfer operator moves unique ownership from fd1 to fd2.
    let fd2 = fd1^

    # Do it again, a use of fd2 after this point will produce an error.
    let fd3 = fd2^

    # We can do this all day...
    let fd4 = fd3^
    fd4.read(...)
    # fd4.__del__() runs here

請注意如何使用後綴“轉移”運算符在擁有該值的各個值之間轉移該值的所有權^，這會破壞先前的綁定並將所有權轉移到新的常量。如果您熟悉 C++，那麼考慮轉移運算符的簡單方法就像std::move，但在這種情況下，我們可以看到它能夠移動事物，而無需將其重置為可以銷毀的狀態：在 C++ 中，如果您的移動運算符無法更改舊值的實例，它將被關閉兩次fd。

Mojo 跟踪值的活躍度並允許您定義自定義移動構造函數。這很少需要，但一旦需要就非常強大。例如，某些類型喜歡llvm::SmallVector type使用“內聯存儲”優化技術，並且它們可能希望通過“內部指針”來實現到其實例中。這是一個眾所周知的技巧，可以減輕 malloc 內存分配器的壓力，但這意味著“移動”操作需要自定義邏輯來在發生這種情況時更新指針。

使用 Mojo，這就像實現自定義__moveinit__方法一樣簡單。這在 C++ 中也很容易實現（不過，在不需要自定義邏輯的情況下可以使用樣板），但在其他流行的內存安全語言中很難實現。

另一點需要注意的是，雖然 Mojo 編譯器提供了良好的可預測性和控制，但它也非常複雜。它保留消除臨時和相應的複制/移動操作的權利。如果這不適合您的類型，您應該使用顯式方法（例如）copy()而不是 dunder 方法。

支持“偷走”的類型
內存安全語言面臨的一個挑戰是，它們需要圍繞編譯器能夠跟踪的內容提供可預測的編程模型，而編譯器中的靜態分析本質上是有限的。例如，雖然編譯器可以理解下面第一個示例中的兩個數組訪問是針對不同的數組元素，但（通常）不可能推理第二個示例（這是 C++ 代碼）：

std::pair<T, T> getValues1(MutableArray<T> &array) {
    return { std::move(array[0]), std::move(array[1]) };
}
std::pair<T, T> getValues2(MutableArray<T> &array, size_t i, size_t j) {
    return { std::move(array[i]), std::move(array[j]) };
}

這裡的問題是根本沒有辦法（僅查看上面的函數體）知道或證明 和 的動態值i不j相同。雖然可以維護動態狀態來跟踪數組的各個元素是否處於活動狀態，但這通常會導致大量的運行時開銷（即使不使用移動/傳輸），而這是 Mojo 和其他系統編程語言不願意做的事情。解決這個問題的方法有很多種，包括一些相當複雜且並不總是容易學習的解決方案。

Mojo 採用務實的方法，讓 Mojo 程序員無需處理其類型系統即可完成工作。如上所示，它並不強制類型可複制、可移動，甚至可構造，但它確實希望類型能夠表達其完整契約，並且它希望實現程序員期望從 C++ 等語言中獲得的流暢設計模式。這裡（眾所周知的）觀察結果是，許多對象的內容可以被“竊取”，而無需禁用其析構函數，這要么是因為它們具有“空狀態”（如可選類型或可為空指針），要么是因為它們具有可高效創建的空值和無操作銷毀（例如，其數據可以具有空指針）  std::vector。

為了支持這些用例，^傳輸運算符支持任意 LValue，並且當應用於其中時，它會調用“竊取移動構造函數”。此構造函數必須將新值設置為活動狀態，並且它可以改變舊值，但它必須將舊值置於其析構函數仍然可以工作的狀態。例如，如果我們想將我們放入FileDescriptor一個向量中並移出它，我們可能會選擇擴展它以知道它-1是一個哨兵，這意味著它是“空”。我們可以這樣實現：

# This is a simple wrapper around POSIX-style fcntl.h functions.
struct FileDescriptor:
    var fd: Int

    # This is the new key capability.
    fn __moveinit__(inout self, inout existing: Self):
        self.fd = existing.fd
        existing.fd = -1  # neutralize 'existing'.

    fn __moveinit__(inout self, owned existing: Self): # as above
    fn __init__(inout self, fd: Int): # as above
    fn __init__(inout self, path: String): # as above

    fn __del__(owned self):
        if self.fd != -1:
            close(self.fd)   # pseudo code, call close(2)

請注意“竊取移動”構造函數如何從現有值中獲取文件描述符並改變該值，以便其析構函數不會執行任何操作。這種技術需要權衡，並不是對每種類型都是最好的。我們可以看到它向析構函數添加了一個（廉價的）分支，因為它必須檢查哨兵情況。通常也認為使此類類型可為空是不好的形式，因為像類型這樣的更通用的功能Optional[T]是處理這種情況的更好方法。

此外，我們計劃在 Mojo 本身中實現Optional[T]，並且Optional需要此功能。我們還相信，庫作者比語言設計者更了解他們的領域問題，並且通常更願意賦予庫作者對該領域的全部權力。因此，您可以選擇（但不必）讓您的類型以選擇加入的方式參與此行為。

可複制類型
可移動類型的下一步是可複制類型。可複制類型也很常見 - 程序員通常期望字符串和數組之類的東西是可複制的，並且每個 Python 對象引用都是可複制的 - 通過複製指針和調整引用計數。

有很多方法可以實現可複制類型。一種可以實現像 Python 或 Java 這樣的引用語義類型，在其中傳播共享指針，一種可以使用易於共享的不可變數據結構，因為它們一旦創建就不會發生變化，一種可以像 Swift 那樣通過惰性寫入時復制來實現深層值語義。這些方法中的每一種都有不同的權衡，Mojo 認為，雖然我們需要一些通用的集合類型集，但我們也可以支持廣泛的專注於特定用例的專用集合類型。

在 Mojo 中，您可以通過實現該__copyinit__方法來做到這一點。這是使用簡單的示例String（偽代碼）：

struct MyString:
    var data: Pointer[UI8]

    # StringRef is a pointer + length and works with StringLiteral.
    def __init__(inout self, input: StringRef):
        self.data = ...

    # Copy the string by deep copying the underlying malloc'd data.
    def __copyinit__(inout self, existing: Self):
        self.data = strdup(existing.data)

    # This isn't required, but optimizes unneeded copies.
    def __moveinit__(inout self, owned existing: Self):
        self.data = existing.data

    def __del__(owned self):
        free(self.data.address)

    def __add__(self, rhs: MyString) -> MyString: ...

這個簡單類型是一個指向用 malloc 分配的“空終止”字符串數據的指針，為清楚起見，使用老式 C API。它實現了__copyinit__，它維護了每個 實例都擁有其底層指針並在銷毀時釋放它的不變式MyString。這個實現建立在我們上面看到的技巧的基礎上，並實現了一個__moveinit__構造函數，這使得它可以在某些常見情況下完全消除臨時副本。您可以在此代碼序列中看到此行為：

fn test_my_string():
    var s1 = MyString("hello ")

    var s2 = s1    # s2.__copyinit__(s1) runs here

    print(s1)

    var s3 = s1^   # s3.__moveinit__(s1) runs here

    print(s2)
    # s2.__del__() runs here
    print(s3)
    # s3.__del__() runs here

在這種情況下，您可以明白為什麼需要復制構造函數：如果沒有復制構造函數，將值複製s1到s2將是一個錯誤 - 因為您不能擁有同一不可複制類型的兩個實時實例。移動構造函數是可選的，但有助於分配到s3：沒有它，編譯器將從 s1 調用複制構造函數，然後銷毀舊s1實例。這在邏輯上是正確的，但會帶來額外的運行時開銷。

Mojo 會急切地銷毀值，這使得它能夠將復制+銷毀對轉換為單個移動操作，這可以帶來比 C++ 更好的性能，而不需要對std::move.

瑣碎類型
最靈活的類型就是“比特袋”。這些類型是“微不足道的”，因為它們可以被複製、移動和銷毀，而無需調用自定義代碼。像這樣的類型可以說是我們周圍最常見的基本類型：像整數和浮點值這樣的東西都是微不足道的。從語言的角度來看，Mojo 不需要對這些進行特殊支持，類型作者將這些東西實現為無操作並允許內聯器讓它們消失是完全可以的。

這種方法不是最理想的有兩個原因：一是我們不希望在簡單類型上定義一堆方法的樣板，二是我們不希望生成和推送一堆函數調用的編譯時開銷，只是讓它們內聯到什麼都沒有。此外，還存在一個正交問題，即許多類型在另一種意義上是微不足道的：它們很小，應該在 CPU 的寄存器中傳遞，而不是間接在內存中傳遞。

因此，Mojo 提供了一個結構裝飾器來解決所有這些問題。您可以使用裝飾器實現類型@register_passable("trivial")，這告訴 Mojo 該類型應該是可複制和可移動的，但它沒有用戶定義的邏輯來執行此操作。它還告訴 Mojo 更喜歡傳遞 CPU 寄存器中的值，這可以帶來效率優勢。

TODO：這個裝飾器需要重新考慮。缺乏自定義邏輯複製/移動/銷毀邏輯和“寄存器中的可傳遞性”是正交的問題，應該分開。前面的邏輯應該包含在一個更通用的@value("trivial")裝飾器中，它與 正交@register_passable。

@value裝飾者
Mojo 的價值生命週期提供了簡單且可預測的鉤子，使您能夠正確表達異國情調的低級事物Atomic。這對於控制和簡單的編程模型來說非常有用，但大多數結構都是其他類型的簡單聚合，我們不想為它們編寫大量樣板文件。為了解決這個問題，Mojo 提供了一個@value結構裝飾器，可以為您合成大量樣板文件。

您可以將其視為@valuePython 的擴展@dataclass，它還可以處理 Mojo__moveinit__和__copyinit__方法。

裝飾@value器會查看您類型的字段，並生成一些缺少的成員。例如，考慮這樣一個簡單的結構：

from String import String

@value
struct MyPet:
    var name: String
    var age: Int

Mojo 會注意到您沒有成員初始化器、移動構造函數或複制構造函數，它會為您合成這些，就像您編寫的一樣：

struct MyPet:
    var name: String
    var age: Int

    fn __init__(inout self, owned name: String, age: Int):
        self.name = name^
        self.age = age

    fn __copyinit__(inout self, existing: Self):
        self.name = existing.name
        self.age = existing.age

    fn __moveinit__(inout self, owned existing: Self):
        self.name = existing.name^
        self.age = existing.age

當您添加@value裝飾器時，Mojo 僅當這些特殊方法不存在時才會合成它們。您可以通過定義自己的版本來覆蓋一個或多個版本的行為。例如，想要自定義復制構造函數但使用默認的成員方式和移動構造函數是相當常見的。

由於結構取得所有權並存儲值，因此 的參數__init__全部作為參數傳遞。owned這是一個有用的微觀優化，可以使用僅移動類型。像這樣的簡單類型Int也可以作為自有值傳遞，但由於這對它們來說沒有任何意義，因此^為了清楚起見，我們省略了標記和傳輸運算符 ( )。

注意：如果您的類型包含任何僅移動字段，Mojo 將不會生成複制構造函數，因為它無法複製這些字段。此外，@value裝飾器僅適用於其成員可複制和/或可移動的類型。如果您Atomic的結構中有類似的內容，那麼它可能不是值類型，並且您無論如何都不想要這些成員。

另請注意，MyPet上面的結構不包括__del__()析構函數 - Mojo 也綜合了它，但它不需要裝飾器（請參閱下面有關析構函數@value的部分）。

此時沒有辦法抑制特定方法的生成或自定義生成，但@value如果有需求，我們可以向生成器添加參數來執行此操作。

由於結構取得所有權並存儲值，因此 的參數__init__全部作為參數傳遞。owned這是一個有用的微觀優化，可以使用僅移動類型。像這樣的簡單類型Int也可以作為自有值傳遞，但由於這對它們來說沒有任何意義，因此^為了清楚起見，我們省略了標記和傳輸運算符 ( )。

析構函數的行為
Mojo 中的任何結構都可以有一個析構函數（一種__del__()方法），該析構函數會在值的生命週期結束時（通常是最後使用該值的時間點）自動運行。例如，一個簡單的字符串可能如下所示（偽代碼）：

@value
struct MyString:
    var data: Pointer[UInt8]

    def __init__(inout self, input: StringRef): ...
    def __add__(self, rhs: String) -> MyString: ...
    def __del__(owned self):
        free(self.data.address)

Mojo使用每次調用後運行的“盡快”MyString (ASAP) 策略來銷毀諸如（它調用析構函數）之類的值。Mojo 不會等到代碼塊結束時才銷毀未使用的值。即使在像這樣的表達式中，一旦不再需要中間表達式，Mojo 就會立即銷毀它們，而不會等到語句結束。__del__()a+b+c+d

當值失效時，Mojo 編譯器會自動調用析構函數，並為析構函數何時運行提供強有力的保證。Mojo 使用靜態編譯器分析來推理代碼並決定何時插入對析構函數的調用。例如：

fn use_strings():
    var a = String("hello a")
    let b = String("hello b")
    print(a)
    # a.__del__() runs here for "hello a"


    print(b)
    # b.__del__() runs here

    a = String("temporary a")
    # a.__del__() runs here because "temporary a" is never used

    # Other stuff happens here

    a = String("final a")
    print(a)
    # a.__del__() runs again here for "final a"

use_strings()

hello a
hello b
final a
在上面的代碼中，您將看到 和a值b是在早期創建的，並且值的每個初始化都與對析構函數的調用相匹配。請注意，它a會被多次銷毀——每次收到新值時都會被銷毀一次。

現在，這可能會讓 C++ 程序員感到驚訝，因為它與RAII 模式不同，在 RAII 模式中，C++ 在作用域末尾銷毀值。Mojo 還遵循這樣的原則：值在構造函數中獲取資源並在析構函數中釋放資源，但 Mojo 中的急切銷毀比 C++ 中基於範圍的銷毀具有許多強大的優勢：

Mojo 方法消除了類型實現重新賦值運算符的需要，例如C++ 中的operator=(const T&)and operator=(T&&)，從而更容易定義類型並消除概念。

Mojo 不允許可變引用與其他可變引用或不可變借用重疊。它提供可預測編程模型的一個主要方法是確保對對象的引用盡快消失，避免編譯器認為一個值可能仍然存在並干擾另一個值的混亂情況，但用戶對此並不清楚。

在最後使用時銷毀值與“移動”優化很好地結合在一起，它將“複製+刪除”對轉換為“移動”操作，這是 C++ 移動優化（如 NRVO）的推廣（稱為返回值優化）。

對於某些常見模式（例如尾遞歸），在 C++ 中銷毀作用域末尾的值是有問題的，因為析構函數調用發生在尾調用之後。對於某些函數式編程模式來說，這可能是一個重大的性能和內存問題。

重要的是，Mojo 的即時銷毀在 Python 風格的def函數中也能很好地工作，以在細粒度級別提供銷毀保證（無需垃圾收集器）——回想一下，Python 並不真正提供超出函數的作用域，因此 Mojo 中的 C++ 風格銷毀的用處要小得多。

注意： Mojo 還支持 Python 風格的with語句，它提供了對資源更有意範圍的訪問。

Mojo 方法與 Rust 和 Swift 的工作方式更相似，因為它們都具有強大的價值所有權跟踪並提供內存安全。一個區別是它們的實現需要使用動態“放置標誌” ——它們維護隱藏的影子變量來跟踪值的狀態以提供安全性。這些通常會被優化掉，但 Mojo 方法完全消除了這種開銷，使生成的代碼更快並避免歧義。

現場敏感的生命週期管理
Mojo 的生命週期分析除了完全控制流感知之外，它還完全字段敏感（結構的每個字段都是獨立跟踪的）。也就是說，Mojo 單獨跟踪“整個對象”是完全還是僅部分初始化/銷毀。

例如，考慮以下代碼：

@value
struct TwoStrings:
    var str1: String
    var str2: String

fn use_two_strings():
    var ts = TwoStrings("foo", "bar")
    print(ts.str1)
    # ts.str1.__del__() runs here

    # Other stuff happens here

    ts.str1 = String("hello") # Overwrite ts.str1
    print(ts.str1)
    # ts.__del__() runs here

use_two_strings()

foo
hello
請注意，該ts.str1字段幾乎立即被銷毀，因為 Mojo 知道它將被下面覆蓋。您還可以在使用轉移運算符時看到這一點，例如：

fn consume(owned arg: String):
    pass

fn use(arg: TwoStrings):
    print(arg.str1)

fn consume_and_use_two_strings():
    var ts = TwoStrings("foo", "bar")
    consume(ts.str1^)
    # ts.str1.__moveinit__() runs here

    # ts is now only partially initialized here!

    ts.str1 = String("hello")  # All together now
    use(ts)                    # This is ok
    # ts.__del__() runs here

consume_and_use_two_strings()

hello
請注意，代碼轉移了該str1字段的所有權：在 的持續時間內other_stuff()，該str1字段完全未初始化，因為所有權已轉移到consume()。然後str1在被use()函數使用之前重新初始化（如果不是，Mojo 會拒絕代碼並顯示未初始化字段錯誤）。

Mojo 對此的規則非常強大且有意直接：字段可以臨時轉移，但“整個對象”必須使用聚合類型的初始值設定項構造並使用聚合析構函數銷毀。這意味著不可能通過僅初始化其字段來創建對象，也不可能通過僅銷毀其字段來拆除對象。例如，以下代碼無法編譯：

fn consume_and_use_two_strings():
    let ts = TwoStrings("foo", "bar") # ts is initialized
    # Uncomment to see an error:
    # consume(ts.str1^)
    # Because `ts` is not used anymore, it should be destroyed here, but
    # the object is not whole, preventing the overall value from being destroyed

    let ts2 : TwoStrings # ts2 type is declared but not initialized
    ts2.str1 = String("foo")
    ts2.str2 = String("bar")  # Both the member are initalized
    # Uncomment to see an error:
    # use(ts2) # Error: 'ts2' isn't fully initialized

雖然我們可以允許這樣的模式發生，但我們拒絕這種情況，因為值不僅僅是其各部分的總和。考慮FileDescriptor包含 POSIX 文件描述符作為整數值的 a ：銷毀整數（無操作）和銷毀FileDescriptor（可能調用close()系統調用）之間存在很大差異。因此，我們要求所有全值初始化都經過初始值設定項並用其全值析構函數銷毀。

就其價值而言，Mojo 內部確實具有與 Rust 函數等效的mem::forget功能，它顯式禁用析構函數，並具有用於“祝福”對象的相應內部功能，但此時它們尚未公開供用戶使用。

現場壽命__init__
方法的行為__init__幾乎與任何其他方法一樣 - 有一點神奇：它知道對象的字段未初始化，但它相信整個對像已初始化。這意味著self一旦所有字段都初始化，您就可以將其用作整個對象：

fn use(arg: TwoStrings2):
    pass

struct TwoStrings2:
    var str1: String
    var str2: String

    fn __init__(inout self, cond: Bool, other: String):
        self.str1 = String()
        if cond:
            self.str2 = other
            use(self)  # Safe to use immediately!
            # self.str2.__del__(): destroyed because overwritten below.

        self.str2 = self.str1
        use(self)  # Safe to use immediately!

類似地，Mojo 中的初始化器完全覆蓋 是安全的self，例如通過委託給其他初始化器：

struct TwoStrings3:
    var str1: String
    var str2: String

    fn __init__(inout self):
        self.str1 = String()
        self.str2 = String()

    fn __init__(inout self, one: String):
        self = TwoStrings3()  # Delegate to the basic init
        self.str1 = one

和owned中參數的字段生命週期__moveinit____del__
移動初始值設定項和析構函數owned的參數存在最後一點魔力。回顧一下，這些方法簽名如下所示：__moveinit__()__del__()

struct TwoStrings:
    ...
    fn __moveinit__(inout self, owned existing: Self):
        # Initializes a new `self` by consuming the contents of `existing`
    fn __del__(owned self):
        # Destroys all resources in `self`

這些方法面臨一個有趣但晦澀難懂的問題：這兩種方法都負責拆解owned existing/self值。也就是說，__moveinit__()銷毀 的子元素以便existing將所有權轉移到新實例，同時__del__()實現其 的刪除邏輯self。因此，他們都希望擁有並轉換該owned值的元素，並且他們絕對不希望該owned值的析構函數也運行（在該方法的情況下__del__()，這將變成無限循環）。

為了解決這個問題，Mojo 專門處理這兩個方法，假設它們的整個值在從方法返回時被銷毀。這意味著在傳輸字段值之前可以使用整個對象。例如，這將按您的預期工作：

fn consume(owned str: String):
    print('Consumed', str)

struct TwoStrings4:
    var str1: String
    var str2: String

    fn __init__(inout self, one: String):
        self.str1 = one
        self.str2 = String("bar")

    fn __moveinit__(inout self, owned existing: Self):
        self.str1 = existing.str1
        self.str2 = existing.str2

    fn __del__(owned self):
        self.dump() # Self is still whole here
        # Mojo calls self.str2.__del__() since str2 isn't used anymore

        consume(self.str1^)
        # str1 has now been transferred;
        # `self.__del__()` is not called (avoiding an infinite loop).
    
    fn dump(inout self):
        print('str1:', self.str1)
        print('str2:', self.str2)

fn use_two_strings():
    let two_strings = TwoStrings4("foo")

# We use a function call to ensure the `two_strings` ownership is enforced
# (Currently, ownership is not enforced for top-level code in notebooks)
use_two_strings()

str1: foo
str2: bar
Consumed foo
您通常不必考慮這一點，但如果您的邏輯具有指向成員的內部指針，則可能需要使它們在析構函數或移動初始值設定項本身中的某些邏輯中保持活動狀態。您可以通過分配_“discard”模式來做到這一點：

fn __del__(owned self):
    self.dump() # Self is still whole here

    consume(self.str1^)
    _ = self.str2
    # self.str2.__del__(): Mojo destroys str2 after its last use.

在這種情況下，如果以某種方式consume()隱式引用某個值str2，這將確保str2直到最後一次使用丟棄模式訪問它時才被銷毀_。

定義析__del__構函數
您應該定義__del__()方法來執行類型所需的任何類型的清理。通常，這包括釋放任何不平凡或不可破壞的字段的內存 - 一旦不再使用任何平凡和可破壞的類型，Mojo 就會自動銷毀它們。

例如，考慮這個結構：

from String import String

struct MyPet:
    var name: String
    var age: Int

    fn __init__(inout self, owned name: String, age: Int):
        self.name = name^
        self.age = age

不需要定義__del__()方法，因為String它是可破壞的（它有自己的__del__()方法），Mojo 一旦不再使用它（即MyPet不再使用實例時）就會銷毀它，並且Int是一個簡單的類型，Mojo 也會盡快回收該內存（儘管有點不同，不需要方法__del__()）。

然而，以下結構必須定義__del__()釋放為其分配的內存的方法Pointer：

struct Array[Type: AnyType]:
    var data: Pointer[Type]
    var size: Int
    var cap: Int

    fn __init__(inout self):
        self.cap = 16
        self.size = 0
        self.data = Pointer[Type].alloc(self.cap)

    fn __init__(inout self, size: Int, value: Type):
        self.cap = size * 2
        self.size = size
        self.data = Pointer[Type].alloc(self.cap)
        for i in range(self.size):
            self.data.store(i, value)

    fn __del__(owned self):
        self.data.free()

生命週期
TODO：解釋返回引用如何工作，與與參數相吻合的生命週期相關聯。該功能尚未啟用。

類型特徵
這是一個非常類似於 Rust 特徵或 Swift 協議或 Haskell 類型類的功能。請注意，這尚未實施。

高級/晦澀的 Mojo 功能
本節介紹對於構建標準庫最底層非常重要的高級用戶功能。這一級別的堆棧包含一些狹窄的功能，需要具備編譯器內部的經驗才能有效地理解和利用。

@register_passable結構裝飾器
處理值的默認模型是它們存在於內存中，因此它們具有標識，這意味著它們間接地傳入和傳出函數（等效地，它們在機器級別“通過引用”傳遞）。這對於無法移動的類型非常有用，並且對於大型對像或具有昂貴複製操作的事物來說是安全的默認值。然而，對於像單個整數或浮點數這樣的微小事物來說，它的效率很低。

為了解決這個問題，Mojo 允許結構體選擇在寄存器中傳遞，而不是使用裝飾器通過內存傳遞@register_passable。Int您將在標準庫中的類型上看到此裝飾器：

@register_passable("trivial")
struct Int:
    var value: __mlir_type.`!pop.scalar<index>`

    fn __init__(value: __mlir_type.`!pop.scalar<index>`) -> Self:
        return Self {value: value}
    ...

基本@register_passable裝飾器不會改變類型的基本行為：它仍然需要有一個__copyinit__可複制的方法，可能仍然有一個__init__and__del__方法等。這個裝飾器的主要影響是在內部實現細節上：@register_passable類型通常在機器寄存器中傳遞（取決於底層架構的細節）。

對於典型的 Mojo 程序員來說，這個裝飾器只有一些可觀察到的效果：

@register_passable類型無法保存不是其本身的類型的實例@register_passable。

類型的實例@register_passable不具有可預測的標識，因此self指針不穩定/不可預測（例如在哈希表中）。

@register_passable參數和結果直接暴露給 C 和 C++，而不是通過指針傳遞。

這種類型的和方法是隱式靜態的（就像在 Python 中一樣），並按值返回其結果__init__而不是採用。__copyinit____new__inout self

我們預計該裝飾器將普遍用於核心標準庫類型，但對於一般應用程序級代碼可以安全地忽略。

上面的例子Int實際上使用了這個裝飾器的“簡單”變體。它改變瞭如上所述的傳遞約定，但也不允許複製和移動構造函數和析構函數（將它們全部簡單地綜合起來）。

TODO：Trivial 需要與其自己的裝飾器解耦，因為它也適用於內存類型。

@always_inline裝飾者
@always_inline("nodebug")：同樣的事情，但沒有調試信息，因此您不會進入 Int 上的 + 方法。

@parameter裝飾者
裝飾@parameter器可以放置在捕獲運行時值的嵌套函數上，以創建“參數”捕獲閉包。這是 Mojo 中的一個不安全功能，因為我們目前沒有對引用捕獲的生命週期進行建模。此功能的一個特殊方面是它允許捕獲運行時值的閉包作為參數值傳遞。

魔術師
C++ 代碼有許多與值生命週期相交的神奇運算符，例如“placement new”、“placement delete”和“operator=”，它們會在現有值上重新分配。當您使用 Mojo 的所有語言功能並在安全結構之上進行組合時，Mojo 是一種安全語言，但任何堆棧都是 C 風格指針和猖獗的不安全性的世界。Mojo 是一種實用語言，由於我們對與 C/C++ 互操作以及直接在 Mojo 本身中實現安全結構（如 String）感興趣，因此我們需要一種方法來表達不安全的事物。

Mojo 標準庫Pointer[element_type]類型是通過 MLIR 中的底層!pop.pointer<element_type>類型實現的，我們希望有一種方法在 Mojo 中實現這些與 C++ 等效的不安全結構。最終，這些將遷移到 Pointer 類型上的所有方法，但在此之前，有些需要作為內置運算符公開。

直接訪問 MLIR
Mojo 提供對 MLIR 方言和生態系統的完全訪問。請查看Mojo 中的低級 IR，了解如何使用__mlir_type、__mlir_op和__mlir_type結構。所有內置和標準庫 API 都是通過調用底層 MLIR 構造來實現的，在這樣做時，Mojo 有效地充當了 MLIR 之上的語法糖。