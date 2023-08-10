# css declaration list

| declaration | w3c description | descriptionCH | how to use | ps | tag |
| ----- | ----- | ----- | ----- | ----- | ----- |
| A | A | A | A | A | A |
| accent-color | Specifies an accent color for user-interface controls | 設定用戶界面控件的強調顏色 | | | |
| align-content | Specifies the alignment between the lines inside a flexible container when the items do not use all available space | 當項目未使用所有可用空間時，指定彈性容器內部行之間的對齊方式 | align-content: * center \| flex-start \| flex-end \| space-between \| space-around \| space-evenly \| **\*stretch** \| initial \| inherit * | 要加 display:flex 才可以使用 | |
| align-items | Specifies the alignment for items inside a flexible container | 指定彈性容器內項目的對齊方式 | | | |
| align-self | Specifies the alignment for selected items inside a flexible container | 指定彈性容器內選定項目的對齊方式 | | | |
| all | Resets all properties (except unicode-bidi and direction) | 重置所有屬性（除unicode-bidi和direction外） | all: *\[global values\]* | | [其他]() |
| animation | A shorthand property for all the animation-* properties | 所有animation-*屬性的簡寫 | animation: **\[time\]** **\[name\]** **\[repet time\]** ***\[anthor function\]*** | 用於創建動畫，需配合@keyframes使用 | [動畫]() |
| animation-delay | Specifies a delay for the start of an animation | 指定動畫開始的延遲 | animation-delay: *\[time\]* | | [動畫]() |
| animation-direction | Specifies whether an animation should be played forwards, backwards or in alternate cycles | 指定動畫是否應正向播放、反向播放或交替播放 | | | [動畫]() |
| animation-duration | Specifies how long an animation should take to complete one cycle | 指定動畫完成一個週期所需的時間 | | | [動畫]() |
| animation-fill-mode | Specifies a style for the element when the animation is not playing (before it starts, after it ends, or both) | 指定元素在動畫未播放時（開始前、結束後或兩者都）的樣式 | | | [動畫]() |
| animation-iteration-count | Specifies the number of times an animation should be played | 指定動畫應播放的次數 | animation-iteration-count: *\[number\] \| infinite* | | [動畫]() |
| animation-name | Specifies a name for the @keyframes animation | 為@keyframes動畫指定名稱 | animation-name: *\[name\]* | | [動畫]() |
| animation-play-state | Specifies whether the animation is running or paused | 指定動畫是否運行或暫停 | | | [動畫]() |
| animation-timing-function | Specifies the speed curve of an animation | 指定動畫的速度曲線 | | | [動畫]() |
| aspect-ratio | Specifies preferred aspect ratio of an element | 指定元素的首選寬高比 | | | |
| B | B | B | B | B | B |
| backdrop-filter | Defines a graphical effect to the area behind an element | 定義在元素後面區域的圖形效果 | | | |
| backface-visibility | Defines whether or not the back face of an element should be visible when facing the user | 定義元素背面在面向用戶時是否可見 | | | |
| background | A shorthand property for all the background-* properties | 所有background-*屬性的簡寫 | background: * (**\[color\]** **\[image\]** **\[attachment\]** **\[repeat\]** (\[positionX?Y?\] \/ \[sizew\] \[sizeh\])?) \| none * | 縮減函式 | [背景]() |
| background-attachment | Sets whether a background image scrolls with the rest of the page, or is fixed | 設定背景圖像是否隨頁面的其餘部分滾動或固定 | background-attachment: *(scroll \| fixed \| local)* | | [背景]() |
| background-blend-mode | Specifies the blending mode of each background layer (color/image) | 指定每個背景圖層（顏色/圖像）的混合模式 | | | [背景]() |
| background-clip | Defines how far the background (color or image) should extend within an element | 定義背景（顏色或圖像）在元素內擴展的程度 | | | [背景]() |
| background-color | Specifies the background color of an element | 指定元素的背景顏色 | background-color: *\[color\]* | | [背景]() |
| background-image | Specifies one or more background images for an element | 為元素指定一個或多個背景圖像 | background-image: url("*\[url\]*") | | [背景]() |
| background-origin | Specifies the origin position of a background image | 指定背景圖像的起始位置 | | | [背景]() |
| background-position | Specifies the position of a background image | 指定背景圖像的位置 | | | [背景]() |
| background-position-x | Specifies the position of a background image on the x-axis | 指定背景圖像在x軸上的位置 | | | [背景]() |
| background-position-y | Specifies the position of a background image on the y-axis | 指定背景圖像在y軸上的位置 | | | [背景]() |
| background-repeat | Sets if/how a background image will be repeated | 設定背景圖像是否/如何重複顯示 | | | [背景]() |
| background-size | Specifies the size of the background images | 指定背景圖像的大小 | | | [背景]() |
| block-size | Specifies the size of an element in block direction | 指定元素在區塊方向上的大小 | | | |
| border | A shorthand property for border-width, border-style and border-color | border-width、border-style和border-color的簡寫 | border: **\[size\]** **\[color\]** ***(\*none \| hidden \| dotted \| dashed \| solid \| double \| groove \| ridge \| inset \| outsetor \| initial \| inherit)*** | 用於設定元素的邊框 | 縮減函式 | [容器]() |
| border-block | A shorthand property for border-block-width, border-block-style and border-block-color | border-block-width、border-block-style和border-block-color的簡寫 | | 縮減函式 | [容器]() |
| border-block-color | Sets the color of the borders at start and end in the block direction | 設定區塊方向上起始和結束處的邊框顏色 | | | [容器]() |
| border-block-end-color | Sets the color of the border at the end in the block direction | 設定區塊方向上結束處的邊框顏色 | | | [容器]() |
| border-block-end-style | Sets the style of the border at the end in the block direction | 設定區塊方向上結束處的邊框樣式 | | | [容器]() |
| border-block-end-width | Sets the width of the border at the end in the block direction | 設定區塊方向上結束處的邊框寬度 | | | [容器]() |
| border-block-start-color | Sets the color of the border at the start in the block direction | 設定區塊方向上起始處的邊框顏色 | | | [容器]() |
| border-block-start-style | Sets the style of the border at the start in the block direction | 設定區塊方向上起始處的邊框樣式 | | | [容器]() |
| border-block-start-width | Sets the width of the border at the start in the block direction | 設定區塊方向上起始處的邊框寬度 | | | [容器]() |
| border-block-style | Sets the style of the borders at start and end in the block direction | 設定區塊方向上起始和結束處的邊框樣式 | | | [容器]() |
| border-block-width | Sets the width of the borders at start and end in the block direction | 設定區塊方向上起始和結束處的邊框寬度 | | | [容器]() |
| border-bottom | A shorthand property for border-bottom-width, border-bottom-style and border-bottom-color | border-bottom-width、border-bottom-style和border-bottom-color的簡寫 | border-bottom: **\[size\]** **\[color\]** ***(\*none \| hidden \| dotted \| dashed \| solid \| double \| groove \| ridge \| inset \| outsetor \| initial \| inherit)*** | 用於設定元素的底部邊框 | 縮減函式 | [容器]() |
| border-bottom-color | Sets the color of the bottom border | 設定底部邊框的顏色 | border-bottom-color: *\[color\]* | | [容器]() |
| border-bottom-left-radius | Defines the radius of the border of the bottom-left corner | 定義左下角的邊框半徑 | border-bottom-left-radius: *\[size\]* | | [容器]() |
| border-bottom-right-radius | Defines the radius of the border of the bottom-right corner | 定義右下角的邊框半徑 | border-bottom-right-radius: *\[size\]* | | [容器]() |
| border-bottom-style | Sets the style of the bottom border | 設定底部邊框的樣式 | border-bottom-style: *\[\***none** \| hidden \| dotted \| dashed \| solid \| double \| groove \| ridge  |\| inset \| outsetor \| initial \| inherit\]* | | [容器]() |
| border-bottom-width | Sets the width of the bottom border | 設定底部邊框的寬度 | border-bottom-width: *\[size\]* | | [容器]() |
| border-collapse | Sets whether table borders should collapse into a single border or be separated | 設定表格邊框是應該合併成單個邊框還是分開 | | | [容器]() |
| border-color | Sets the color of the four borders | 設定四個邊框的顏色 | border-color: *\[color\]* | | [容器]() |
| border-image | A shorthand property for all the border-image-* properties | 所有border-image-*屬性的簡寫 | | 縮減函式 | [容器]() |
| border-image-outset | Specifies the amount by which the border image area extends beyond the border box | 指定邊框圖像區域擴展超出邊框盒的量 | | | [容器]() |
| border-image-repeat | Specifies whether the border image should be repeated, rounded or stretched | 指定邊框圖像是否應重複、圓角或拉伸 | | | [容器]() |
| border-image-slice | Specifies how to slice the border image | 指定如何切割邊框圖像 | | | [容器]() |
| border-image-source | Specifies the path to the image to be used as a border | 指定用作邊框的圖像的路徑 | | | [容器]() |
| border-image-width | Specifies the width of the border image | 指定邊框圖像的寬度 | | | [容器]() |
| border-inline | A shorthand property for border-inline-width, border-inline-style and border-inline-color | border-inline-width、border-inline-style和border-inline-color的簡寫 | | 縮減函式 | [容器]() |
| border-inline-color | Sets the color of the borders at start and end in the inline direction | 設定內聯方向上起始和結束處的邊框顏色 | | | [容器]() |
| border-inline-end-color | Sets the color of the border at the end in the inline direction | 設定內聯方向上結束處的邊框顏色 | | | [容器]() |
| border-inline-end-style | Sets the style of the border at the end in the inline direction | 設定內聯方向上結束處的邊框樣式 | | | [容器]() |
| border-inline-end-width | Sets the width of the border at the end in the inline direction | 設定內聯方向上結束處的邊框寬度 | | | [容器]() |
| border-inline-start-color | Sets the color of the border at the start in the inline direction | 設定內聯方向上起始處的邊框顏色 | | | [容器]() |
| border-inline-start-style | Sets the style of the border at the start in the inline direction | 設定內聯方向上起始處的邊框樣式 | | | [容器]() |
| border-inline-start-width | Sets the width of the border at the start in the inline direction | 設定內聯方向上起始處的邊框寬度 | | | [容器]() |
| border-inline-style | Sets the style of the borders at start and end in the inline direction | 設定內聯方向上起始和結束處的邊框樣式 | | | [容器]() |
| border-inline-width | Sets the width of the borders at start and end in the inline direction | 設定內聯方向上起始和結束處的邊框寬度 | | | [容器]() |
| border-left | A shorthand property for all the border-left-\* properties | border-left-\*屬性的簡寫 | border-left: **\[size\]** **\[color\]** ***(\*none \| hidden \| dotted \| dashed \| solid \| double \| groove \| ridge \| inset \| outsetor \| initial \| inherit)*** | 用於設定元素的左邊框 | 縮減函式 | [容器]() |
| border-left-color | Sets the color of the left border | 設定左邊框的顏色 | border-left-color: *\[color\]* | | [容器]() |
| border-left-style | Sets the style of the left border | 設定左邊框的樣式 | border-left-style: *\[\***none** \| hidden \| dotted \| dashed \| solid \| double \| groove \| ridge \| inset \| outsetor \| initial \| inherit\]* | | [容器]() |
| border-left-width | Sets the width of the left border | 設定左邊框的寬度 | border-left-width: *\[size\]* | | [容器]() |
| border-radius | A shorthand property for the four border-\*-radius properties | 四個border-\*-radius屬性的簡寫 | border-radius: *\[size\]* | 用於設定元素的圓角邊框 | 縮減函式 | [容器]() |
| border-right | A shorthand property for all the border-right-* properties | border-right-*屬性的簡寫 | border-right: **\[size\]** **\[color\]** ***(\*none \| hidden \| dotted \| dashed \| solid \| double \| groove \| ridge \| inset \| outsetor \| initial \| inherit)*** | 用於設定元素的右邊框 | 縮減函式 | [容器]() |
| border-right-color | Sets the color of the right border | 設定右邊框的顏色 | border-right-color: *\[color\]* | | [容器]() |
| border-right-style | Sets the style of the right border | 設定右邊框的樣式 | border-right-style: *\[\***none** \| hidden \| dotted \| dashed \| solid \| double \| groove \| ridge \| inset \| outsetor \| initial \| inherit\]* | | [容器]() |
| border-right-width | Sets the width of the right border | 設定右邊框的寬度 | border-right-width: *\[size\]* | | [容器]() |
| border-spacing | Sets the distance between the borders of adjacent cells | 設定相鄰單元格之間的邊框間距 | | | [容器]() |
| border-style | Sets the style of the four borders | 設定四個邊框的樣式 | border-style: *\[\***none** \| hidden \| dotted \| dashed \| solid \| double \| groove \| ridge \| inset \| outsetor \| initial \| inherit\]* | | [容器]() |
| border-top | A shorthand property for border-top-width, border-top-style and border-top-color | border-top-width、border-top-style和border-top-color的簡寫 | **\[size\]** **\[color\]** ***(\*none \| hidden \| dotted \| dashed \| solid \| double \| groove \| ridge \| inset \| outsetor \| initial \| inherit)*** | 用於設定元素的頂部邊框 | 縮減函式 | [容器]() |
| border-top-color | Sets the color of the top border | 設定頂部邊框的顏色 | border-top-color: *\[color\]*  | | [容器]() |
| border-top-left-radius | Defines the radius of the border of the top-left corner | 定義左上角的邊框半徑 | border-top-left-radius: *\[size\]* | | [容器]() |
| border-top-right-radius | Defines the radius of the border of the top-right corner | 定義右上角的邊框半徑 | border-top-right-radius: *\[size\]* | | [容器]() |
| border-top-style | Sets the style of the top border | 設定頂部邊框的樣式 | border-top-style: *\[\***none** \| hidden \| dotted \| dashed \| solid \| double \| groove \| ridge \| inset \| outsetor \| initial \| inherit\]* | | [容器]() |
| border-top-width | Sets the width of the top border | 設定頂部邊框的寬度 | border-top-width: *\[size\]* | | [容器]() |
| border-width | Sets the width of the four borders | 設定四個邊框的寬度 | border-width: *\[size\]* | | [容器]() |
| bottom | Sets the bottom edge position of a positioned element | 設定定位元素的底部邊緣位置 | bottom: *\[length\]* \| *\[percentage\]* \| *auto* | 用於設定元素底部位置 | 縮減函式 | [定位]() |
| box-decoration-break | Specifies how an element's background, padding, border, border-image, box-shadow, margin, and clip-path apply when an element is broken across multiple lines, columns, or pages | 指定元素在跨多行、列或頁面分割時，背景、填充、邊框、邊框圖像、框陰影、邊距和剪裁路徑的應用方式 | | | |
| box-shadow | Attaches one or more drop-shadows to the box | 附加一個或多個投影到框上 | box-shadow: **\[h-shadow\]** **\[v-shadow\]** **\[blur\]** **\[spread\]** **\[color\]** **\[inset\]** | 用於添加元素的框陰影 | 縮減函式 | [外觀]() |
| box-sizing | Defines how the width and height of an element are calculated | 定義如何計算元素的寬度和高度 | | | [外觀]() |
| break-after | Sets the behavior of a page break after an element | 設定元素後的分頁行為 | | | [分頁]() |
| break-before | Sets the behavior of a page break before an element | 設定元素前的分頁行為 | | | [分頁]() |
| break-inside | Sets the behavior of a page break inside an element | 設定元素內的分頁行為 | | | [分頁]() |
| C | C | C | C | C | C |
| caption-side | Specifies the placement of a table caption | | | | |
| caret-color | Specifies the color of the cursor (caret) in inputs, textareas, or any element that is editable | | | | |
| clear | Specifies what should happen with the element that is next to a floating element | | | | |
| clip | Clips an absolutely positioned element | | | | |
| color | Sets the color of text | 文字顏色 | color: *\[color\]* | | |
| column-count | Specifies the number of columns an element should be divided into | | | | |
| column-fill | Specifies how to fill columns, balanced or not | | | | |
| column-gap | Specifies the gap between the columns | | | | |
| column-rule | A shorthand property for all the column-rule-* properties | | | | |
| column-rule-color | Specifies the color of the rule between columns | | | | |
| column-rule-style | Specifies the style of the rule between columns | | | | |
| column-rule-width | Specifies the width of the rule between columns | | | | |
| column-span | Specifies how many columns an element should span across | | | | |
| column-width | Specifies the column width | | | | |
| columns | A shorthand property for column-width and column-count | | | | |
| content | Used with the :before and :after pseudo-elements, to insert generated content | 使用css顯示文字 | context: "*\[context\]*" | 須搭配before或after使用 | |
| counter-increment | Increases or decreases the value of one or more CSS counters | | | | |
| counter-reset | Creates or resets one or more CSS counters | | | | |
| cursor | Specifies the mouse cursor to be displayed when pointing over an element | 滑鼠指標樣式 | cursor: *[cursorlist](cursordef.md)* | | |
| D | D | D | D | D | D |
| direction | Specifies the text direction/writing direction | 文字方向 | direction: *(\***ltr** \| rtl \| inherit \| initial \| revert \| revert-layer \| unset)* | | |
| display | Specifies how a certain HTML element should be displayed | | | | |
| E | E | E | E | E | E |
| empty-cells | Specifies whether or not to display borders and background on empty cells in a table | | | | |
| F | F | F | F | F | F |
| filter | Defines effects (e.g. blurring or color shifting) on an element before the element is displayed | 濾鏡效果 | | | |
| flex | A shorthand property for the flex-grow, flex-shrink, and the flex-basis properties | | | | |
| flex-basis | Specifies the initial length of a flexible item | | | | |
| flex-direction | Specifies the direction of the flexible items | | | | |
| flex-flow | A shorthand property for the flex-direction and the flex-wrap properties | | | | |
| flex-grow | Specifies how much the item will grow relative to the rest | | | | |
| flex-shrink | Specifies how the item will shrink relative to the rest | | | | |
| flex-wrap | Specifies whether the flexible items should wrap or not | | | | |
| float | Specifies whether an element should float to the left, right, or not at all | | | | |
| font | A shorthand property for the font-style, font-variant, font-weight, font-size/line-height, and the font-family properties | 文字設定 | font: *\[size\]* * (/ \[line-height\] \| \[weight\] \| \[style\] \| \[variant\])? * *\[family\]* | 縮減函式 | |
| font-family | Specifies the font family for text | 文字自型 | font-family: *\[family1\]* *\[family2\]* *\[family inf..\]* | 先以第一個為如果沒有字型則換下一個以此類推 | |
| font-feature-settings | Allows control over advanced typographic features in OpenType fonts | | | | |
| font-kerning | Controls the usage of the kerning information (how letters are spaced) | | | | |
| font-language-override | Controls the usage of language-specific glyphs in a typeface | | | | |
| font-size | Specifies the font size of text | 文字大小 | font-size: *\[size\]* \| *(xx-small \| x-small \| small \| medium \| large \| x-large \| xx-large \| smaller \| larger)* | | |
| font-size-adjust | Preserves the readability of text when font fallback occurs | | | | |
| font-stretch | Selects a normal, condensed, or expanded face from a font family | | | | |
| font-style | Specifies the font style for text | | | | |
| font-synthesis | Controls which missing typefaces (bold or italic) may be synthesized by the browser | 文字變體 | | | |
| font-variant | Specifies whether or not a text should be displayed in a small-caps font | | | | |
| font-variant-alternates | Controls the usage of alternate glyphs associated to alternative names defined in @font-feature-values | | | | |
| font-variant-caps | Controls the usage of alternate glyphs for capital letters | | | | |
| font-variant-east-asian | Controls the usage of alternate glyphs for East Asian scripts (e.g Japanese and Chinese) | | | | |
| font-variant-ligatures | Controls which ligatures and contextual forms are used in textual content of the elements it applies to | | | | |
| font-variant-numeric | Controls the usage of alternate glyphs for numbers, fractions, and ordinal markers | | | | |
| font-variant-position | Controls the usage of alternate glyphs of smaller size positioned as superscript or subscript regarding the baseline of the font | | | | |
| font-weight | Specifies the weight of a font | 文字粗度 | | | |
| G | G | G | G | G | G |
| gap | A shorthand property for the row-gap and the column-gap properties | | | | |
| grid | A shorthand property for the grid-template-rows, grid-template-columns, grid-template-areas, grid-auto-rows, grid-auto-columns, and the grid-auto-flow properties | 網格系統 | | | [網格](grid.md) |
| grid-area | Either specifies a name for the grid item, or this property is a shorthand property for the grid-row-start, grid-column-start, grid-row-end, and grid-column-end properties| | | | [網格](grid.md) |
| grid-auto-columns | Specifies a default column size | | | | [網格](grid.md) |
| grid-auto-flow | Specifies how auto-placed items are inserted in the grid | | | | [網格](grid.md) |
| grid-auto-rows | Specifies a default row size | | | | [網格](grid.md) |
| grid-column | A shorthand property for the grid-column-start and the grid-column-end properties | | | | [網格](grid.md) |
| grid-column-end | Specifies where to end the grid item | | | | [網格](grid.md) |
| grid-column-gap | Specifies the size of the gap between columns | | | | [網格](grid.md) |
| grid-column-start | Specifies where to start the grid item | | | | [網格](grid.md) |
| grid-gap | A shorthand property for the grid-row-gap and grid-column-gap properties | | | | [網格](grid.md) |
| grid-row | A shorthand property for the grid-row-start and the grid-row-end properties | | | | [網格](grid.md) |
| grid-row-end | Specifies where to end the grid item | | | | [網格](grid.md) |
| grid-row-gap | Specifies the size of the gap between rows | | | | [網格](grid.md) |
| grid-row-start | Specifies where to start the grid item | | | | [網格](grid.md) |
| grid-template | A shorthand property for the grid-template-rows, grid-template-columns and grid-areas properties | | | | [網格](grid.md) |
| grid-template-areas | Specifies how to display columns and rows, using named grid items | | | | [網格](grid.md) |
| grid-template-columns | Specifies the size of the columns, and how many columns in a grid layout | | | | [網格](grid.md) |
| grid-template-rows | Specifies the size of the rows in a grid layout | | | | [網格](grid.md) |
| H | H | H | H | H | H |
| hanging-punctuation | Specifies whether a punctuation character may be placed outside the line box | | | | |
| height | Sets the height of an element | 物件高度 | height: *\[size\]* | | [定位]() |
| hyphens | Sets how to split words to improve the layout of paragraphs | | | | |
| I | I | I | I | I | I |
| image-rendering | Specifies the type of algorithm to use for image scaling | | | | |
| inline-size | Specifies the size of an element in the inline direction | | | | |
| inset | Specifies the distance between an element and the parent element | | | | |
| inset-block | Specifies the distance between an element and the parent element in the block direction | | | | |
| inset-block-end | Specifies the distance between the end of an element and the parent element in the block direction | | | | |
| inset-block-start | Specifies the distance between the start of an element and the parent element in the block direction | | | | |
| inset-inline | Specifies the distance between an element and the parent element in the inline direction | | | | |
| inset-inline-end | Specifies the distance between the end of an element and the parent element in the inline direction | | | | |
| inset-inline-start | Specifies the distance between the start of an element and the parent element in the inline direction | | | | |
| isolation | Defines whether an element must create a new stacking content | | | | |
| J | J | J | J | J | J |
| justify-content | Specifies the alignment between the items inside a flexible container when the items do not use all available space | | | | |
| justify-items | Is set on the grid container. Specifies the alignment of grid items in the inline direction | | | | |
| justify-self | Is set on the grid item. Specifies the alignment of the grid item in the inline direction | | | | |
| K | K | K | K | K | K |
| none | none | none | none | none | none |
| L | L | L | L | L | L |
| left | Specifies the left position of a positioned element | 距左邊之單位長 | left: *\[size\]* | 須搭配position使用 | [定位]() |
| letter-spacing | Increases or decreases the space between characters in a text | 文字間格 | | | [文字]() |
| line-break | Specifies how/if to break lines | 換行設定 | | | [文字]() |
| line-height | Sets the line height | 行高 | line-height: *\[size\]* | | [文字]() |
| list-style | Sets all the properties for a list in one declaration | 清單設定 | | 縮減函式 | [表單]() |
| list-style-image | Specifies an image as the list-item marker | 清單圖片 | list-style-image: url("*\[url\]*") | | [表單]() |
| list-style-position | Specifies the position of the list-item markers (bullet points) | 清單定位 | list-style-position: *\[size\]* | | [表單]() |
| list-style-type | Specifies the type of list-item marker | 清單樣式 | list-style-type: ** | | [表單]() |
| M | M | M | M | M | M |
| margin | Sets all the margin properties in one declaration | 外距設定 | | 縮減函式 | [容器]() |
| margin-block | Specifies the margin in the block direction | | | | |
| margin-block-end | Specifies the margin at the end in the block direction | | | | |
| margin-block-start | Specifies the margin at the start in the block direction | | | | |
| margin-bottom | Sets the bottom margin of an element | 下外距 | margin-bottom: *\[size\]* | | [容器]() |
| margin-inline | Specifies the margin in the inline direction | | | | |
| margin-inline-end | Specifies the margin at the end in the inline direction | | | | |
| margin-inline-start | Specifies the margin at the start in the inline direction | | | | |
| margin-left | Sets the left margin of an element | 左外距 | margin-left: *\[size\]* | | [容器]() |
| margin-right | Sets the right margin of an element | 右外距 | margin-right: *\[size\]* | | [容器]() |
| margin-top | Sets the top margin of an element | 上外距 | margin-top: *\[size\]* | | [容器]() |
| mask | Hides parts of an element by masking or clipping an image at specific places | | | | |
| mask-clip | Specifies the mask area | | | | |
| mask-composite | Represents a compositing operation used on the current mask layer with the mask layers below it | | | | |
| mask-image | Specifies an image to be used as a mask layer for an element |1 | | | |
| mask-mode | Specifies whether the mask layer image is treated as a luminance mask or as an alpha mask | | | | |
| mask-origin | Specifies the origin position (the mask position area) of a mask layer image | | | | |
| mask-position | Sets the starting position of a mask layer image (relative to the mask position area) | | | | |
| mask-repeat | Specifies how the mask layer image is repeated | | | | |
| mask-size | Specifies the size of a mask layer image | | | | |
| mask-type | Specifies whether an SVG &lt;mask&gt; element is treated as a luminance mask or as an alpha mask | | | | |
| max-height | Sets the maximum height of an element | 最大高度 | max-height: *\[size\]* \| *auto* | | [定位]() |
| max-width | Sets the maximum width of an element | 最大寬度 | max-width: *\[size\]* \| *auto* | | [定位]() |
| max-block-size | Sets the maximum size of an element in the block direction | | | | |
| max-inline-size | Sets the maximum size of an element in the inline direction | | | | |
| min-block-size | Sets the minimum size of an element in the block direction | | | | |
| min-inline-size | Sets the minimum size of an element in the inline direction | | | | |
| min-height | Sets the minimum height of an element | 最小高度 | min-height: *\[size\]* \| *auto* | | [定位]() |
| min-width | Sets the minimum width of an element | 最小寬度 | min-width: *\[size\]* \| *auto* | | [定位]() |
| mix-blend-mode | Specifies how an element's content should blend with its direct parent background | | | | |
| O | O | O | O | O | O |
| object-fit | Specifies how the contents of a replaced element should be fitted to the box established by its used height and width | | | | |
| object-position | Specifies the alignment of the replaced element inside its box | | | | |
| offset | Is a shorthand, and specifies how to animate an element along a path | | | | |
| offset-anchor | Specifies a point on an element that is fixed to the path it is animated along | | | | |
| offset-distance | Specifies the position along a path where an animated element is placed | | | | |
| offset-path | Specifies the path an element is animated along | | | | |
| offset-rotate | Specifies rotation of an element as it is animated along a path | | | | |
| opacity | Sets the opacity level for an element | 不透明度 | opacity: 0=~=1 \| 0=~=100% | | [容器]() |
| order | Sets the order of the flexible item, relative to the rest | | | | |
| orphans | Sets the minimum number of lines that must be left at the bottom of a page or column | | | | |
| outline | A shorthand property for the outline-width, outline-style, and the outline-color properties | 外框線 | | 縮減函式 | |
| outline-color | Sets the color of an outline | 外框線顏色 | | | |
| outline-offset | Offsets an outline, and draws it beyond the border edge | 外框線 | | | |
| outline-style | Sets the style of an outline | 外框線樣式 | | | |
| outline-width | Sets the width of an outline | 外框線大小 | | | |
| overflow | Specifies what happens if content overflows an element's box | 物件溢位設定 | overflow: * **\*visable** \| hidden \| scroll \| auto \| clip * (* **\*visable** \| hidden \| scroll \| auto \| clip *)? | 縮減函式 | [容器]() |
| overflow-anchor | Specifies whether or not content in viewable area in a scrollable contianer should be pushed down when new content is loaded above | | | | |
| overflow-wrap | Specifies whether or not the browser can break lines with long words, if they overflow the container | | | | |
| overflow-x | Specifies whether or not to clip the left/right edges of the content, if it overflows the element's content area | 物件x軸溢位設定 | overflow-x: * **\*visable** \| hidden \| scroll \| auto \| clip * | | [容器]() |
| overflow-y | Specifies whether or not to clip the top/bottom edges of the content, if it overflows the element's content area | 物件y軸溢位設定 | overflow-y: * **\*visable** \| hidden \| scroll \| auto \| clip * | | [容器]() |
| overscroll-behavior | Specifies whether to have scroll chaining or overscroll affordance in x- and y-directions | | | | |
| overscroll-behavior-block | Specifies whether to have scroll chaining or overscroll affordance in the block direction | | | | |
| overscroll-behavior-inline | Specifies whether to have scroll chaining or overscroll affordance in the inline direction | | | | |
| overscroll-behavior-x | Specifies whether to have scroll chaining or overscroll affordance in x-direction | | | | |
| overscroll-behavior-y | Specifies whether to have scroll chaining or overscroll affordance in y-directions | | | | |
| P | P | P | P | P | P |
| padding | A shorthand property for all the padding-* properties | 內距設定 | padding: *\[udlr size\]* \| *\[ud size\] \[lr size\]* \| *\[u size\] \[lr size\] \[d size\]* \| *\[u size\] \[r size\] \[d size\] \[l size\]* | 縮減函式 | [容器]() |
| padding-block | Specifies the padding in the block direction | | | | |
| padding-block-end | Specifies the padding at the end in the block direction | | | | |
| padding-block-start | Specifies the padding at the start in the block direction | | | | |
| padding-bottom | Sets the bottom padding of an element | 下內距 | padding-bottom: *\[size\]* | | [容器]() |
| padding-inline | Specifies the padding in the inline direction | | | | |
| padding-inline-end | Specifies the padding at the end in the inline direction | | | | |
| padding-inline-start | Specifies the padding at the start in the inline direction | | | | |
| padding-left | Sets the left padding of an element | 左內距 | padding-left: *\[size\]* | | [容器]() |
| padding-right | Sets the right padding of an element | 右內距 | padding-right: *\[size\]* | | [容器]() |
| padding-top | Sets the top padding of an element | 上內距 | padding-top: *\[size\]* | | [容器]() |
| page-break-after | Sets the page-break behavior after an element | | | | |
| page-break-before | Sets the page-break behavior before an element | | | | |
| page-break-inside | Sets the page-break behavior inside an element | | | | |
| paint-order | Sets the order of how an SVG element or text is painted. | | | | |
| perspective | Gives a 3D-positioned element some perspective | | | | |
| perspective-origin | Defines at which position the user is looking at the 3D-positioned element | | | | |
| place-content | Specifies align-content and justify-content property values for flexbox and grid layouts | | | | |
| place-items | Specifies align-items and justify-items property values for grid layouts | | | | |
| place-self | Specifies align-self and justify-self property values for grid layouts | | | | |
| pointer-events | Defines whether or not an element reacts to pointer events | | | | |
| position | Specifies the type of positioning method used for an element (static, relative, absolute or fixed) | 定位設定 | position: *absolute* \| *fixed* \| *relative* \| *staic* \| *sticky* | | [定位]() |
| Q | Q | Q | Q | Q | Q |
| quotes | Sets the type of quotation marks for embedded quotations | | | | |
| R | R | R | R | R | R |
| resize | Defines if (and how) an element is resizable by the user | | | | |
| right | Specifies the right position of a positioned element | 距右邊之單位長 | right: *\[size\]* | 須搭配position使用 | [定位]() |
| rotate | Specifies the rotation of an element | 物件旋轉角度 | rotate: *\[x,y,z\]* *\[size\]* \| *none* | | [定位]() |
| row-gap | Specifies the gap between the grid rows | | | | |
| S | S | S | S | S | S |
| scale | Specifies the size of an element by scaling up or down | | | | |
| scroll-behavior | Specifies whether to smoothly animate the scroll position in a scrollable box, instead of a straight jump | | | | |
| scroll-margin | Specifies the margin between the snap position and the container | | | | |
| scroll-margin-block | Specifies the margin between the snap position and the container in the block direction | | | | |
| scroll-margin-block-end | Specifies the end margin between the snap position and the container in the block direction | | | | |
| scroll-margin-block-start | Specifies the start margin between the snap position and the container in the block direction | | | | |
| scroll-margin-bottom | Specifies the margin between the snap position on the bottom side and the container | | | | |
| scroll-margin-inline | Specifies the margin between the snap position and the container in the inline direction | | | | |
| scroll-margin-inline-end | Specifies the end margin between the snap position and the container in the inline direction | | | | |
| scroll-margin-inline-start | Specifies the start margin between the snap position and the container in the inline direction | | | | |
| scroll-margin-left | Specifies the margin between the snap position on the left side and the container | | | | |
| scroll-margin-right | Specifies the margin between the snap position on the right side and the container | | | | |
| scroll-margin-top | Specifies the margin between the snap position on the top side and the container | | | | |
| scroll-padding | Specifies the distance from the container to the snap position on the child elements | | | | |
| scroll-padding-block | Specifies the distance in block direction from the container to the snap position on the child elements | | | | |
| scroll-padding-block-end | Specifies the distance in block direction from the end of the container to the snap position on the child elements | | | | |
| scroll-padding-block-start | Specifies the distance in block direction from the start of the container to the snap position on the child elements | | | | |
| scroll-padding-bottom | Specifies the distance from the bottom of the container to the snap position on the child elements | | | | |
| scroll-padding-inline | Specifies the distance in inline direction from the container to the snap position on the child elements | | | | |
| scroll-padding-inline-end | Specifies the distance in inline direction from the end of the container to the snap position on the child elements | | | | |
| scroll-padding-inline-start | Specifies the distance in inline direction from the start of the container to the snap position on the child elements | | | | |
| scroll-padding-left | Specifies the distance from the left side of the container to the snap position on the child elements | | | | |
| scroll-padding-right | Specifies the distance from the right side of the container to the snap position on the child elements | | | | |
| scroll-padding-top | Specifies the distance from the top of the container to the snap position on the child elements | | | | |
| scroll-snap-align | Specifies where to position elements when the user stops scrolling | | | | |
| scroll-snap-stop | Specifies scroll behaviour after fast swipe on trackpad or touch screen | | | | |
| scroll-snap-type | Specifies how snap behaviour should be when scrolling | | | | |
| scrollbar-color | Specifies the color of the scrollbar of an element | | | | |
| T | T | T | T | T | T |
| tab-size | Specifies the width of a tab character | | | | |
| table-layout | Defines the algorithm used to lay out table cells, rows, and columns | | | | |
| text-align | Specifies the horizontal alignment of text | 文字設定 | text-align:  *start* \| *end*\| *left*\| *right*\| *center*\| *justify*\| *justify-all*\| *match-parent* | | [文字]() |
| text-align-last | Describes how the last line of a block or a line right before a forced line break is aligned when text-align is "justify" | | | | |
| text-combine-upright | Specifies the combination of multiple characters into the space of a single character | | | | |
| text-decoration | Specifies the decoration added to text | | | | |
| text-decoration-color | Specifies the color of the text-decoration | | | | |
| text-decoration-line | Specifies the type of line in a text-decoration | | | | |
| text-decoration-style | Specifies the style of the line in a text decoration | | | | |
| text-decoration-thickness | Specifies the thickness of the decoration line | | | | |
| text-emphasis | Applies emphasis marks to text | | | | |
| text-indent | Specifies the indentation of the first line in a text-block | 首行縮排 | text-indent: *\[size\]* \| *auto* | | [文字]() |
| text-justify | Specifies the justification method used when text-align is "justify" | | | | |
| text-orientation | Defines the orientation of characters in a line | | | | |
| text-overflow | Specifies what should happen when text overflows the containing element | | | | |
| text-shadow | Adds shadow to text | 文字陰影 | | | |
| text-transform | Controls the capitalization of text | | | | |
| text-underline-position | Specifies the position of the underline which is set using the text-decoration property | | | | |
| top | Specifies the top position of a positioned element | 距頂部之單位長 | top: *\[size\]* | 須搭配position使用 | [定位]() |
| transform | Applies a 2D or 3D transformation to an element | | | | |
| transform-origin | Allows you to change the position on transformed elements | | | | |
| transform-style | Specifies how nested elements are rendered in 3D space | | | | |
| transition | A shorthand property for all the transition-* properties | | | | |
| transition-delay | Specifies when the transition effect will start | | | | |
| transition-duration | Specifies how many seconds or milliseconds a transition effect takes to complete | | | | |
| transition-property | Specifies the name of the CSS property the transition effect is for | | | | |
| transition-timing-function | Specifies the speed curve of the transition effect | | | | |
| translate | Specifies the position of an element | | | | |
| U | U | U | U | U | U |
| unicode-bidi | Used together with the direction property to set or return whether the text should be overridden to support multiple languages in the same document | | | | |
| user-select | Specifies whether the text of an element can be selected | | | | |
| V | V | V | V | V | V |
| vertical-align | Sets the vertical alignment of an element | | | | |
| visibility | Specifies whether or not an element is visible | | | | |
| W | W | W | W | W | W |
| white-space | Specifies how white-space inside an element is handled | | | | |
| widows | Sets the minimum number of lines that must be left at the top of a page or column | | | | |
| width | Sets the width of an element | | | | |
| word-break | Specifies how words should break when reaching the end of a line | | | | |
| word-spacing | Increases or decreases the space between words in a text | | | | |
| word-wrap | Allows long, unbreakable words to be broken and wrap to the next line | | | | |
| writing-mode | Specifies whether lines of text are laid out horizontally or vertically | | | | |
| X | X | X | X | X | X |
| none | none | none | none | none | none |
| Y | Y | Y | Y | Y | Y |
| none | none | none | none | none | none |
| Z | Z | Z | Z | Z | Z |
| z-index | Sets the stack order of a positioned element | 物件階層 | z-index: *\[number\]* | | [容器]() |
| @ | @ | @ | @ | @ | @ |
| @charset | Specifies the character encoding used in the style sheet | | | | [文字]() |
| @font-face | A rule that allows websites to download and use fonts other than the "web-safe" fonts | | | | [文字]() |
| @font-feature-values | Allows authors to use a common name in font-variant-alternate for feature activated differently in OpenType | | | | [文字]() |
| @import | Allows you to import a style sheet into another style sheet | 匯入其他樣式表 | | | |
| @keyframes | Specifies the animation code | 關鍵影格設定 | @keyframes *\[name\]*{ /\* *context* \*/ } | | [動畫]() |
| @media | Sets the style rules for different media types/devices/sizes | | | | |
| | | pseudo | element | | |
| ::after | | | | | |
| ::backdrop | | | | | |
| ::before | | | | | |
| ::cue | | | | | |
| ::cue-region | | | | | |
| ::first-letter | | | | | |
| ::first-line | | | | | |
| ::file-selector-button | | | | | |
| ::grammar-error | | | | 實驗性功能 | |
| ::marker | | | | | |
| ::part() | | | | | |
| ::placeholder | | | | | |
| ::selection | | | | | |
| ::slotted() | | | | | |
| ::spelling-error | | | | 實驗性功能 | |
| ::target-text | | | | 實驗性功能 | |
| | | pseudo | classes | | |
| :active | | | | | |
| :any | | | | | |
| :checked | | 已勾選事件 | *checkbox \| radio \| option @ \| label*:checked{ /\* declaration \*/ } | | |
| :default | | | | | |
| :dir() | | | | | |
| :disabled | | 禁用之區塊事件 | *input: \| select \| textarea \[type="disabled"\]*:disabled{ /\* declaration \*/ } | | |
| :empty | | | | | |
| :enabled | | 啟用之區塊事件 | | | |
| :first | | | | | |
| :first-child | | | | | |
| :first-of-type | | | | | |
| :fullscreen | | | | | |
| :focus | | | | | |
| :hover | | 滑鼠覆蓋事件 | *selector*:hover{ /* declaration */ } | | |
| :indeterminate | | | | | |
| :in-range | | | | | |
| :invalid | | | | | |
| :lang() | | | | | |
| :last-child | | | | | |
| :last-of-type | | | | | |
| :left | | | | | |
| :link | | | | | |
| :not() | | | | | |
| :nth-child() | | | | | |
| :nth-last-child() | | | | | |
| :nth-last-of-type() | | | | | |
| :nth-of-type() | | | | | |
| :only-child | | | | | |
| :only-of-type | | | | | |
| :optional | | | | | |
| :out-of-range | | | | | |
| :read-only | | 唯讀之區塊事件 | *input: \| textarea \[type="readonly"\]*:disabled{ /\* declaration \*/ } | | |
| :read-write | | | | | |
| :required | | 必填之區塊事件 | *input: \| select \| textarea \[type="required"\]*:required{ /\* declaration \*/ } | | |
| :right | | | | | |
| :root | | | | | |
| :scope | | | | | |
| :target | | | | | |
| :valid | | | | | |
| :visited | | | | | |

## 註解及參見
因通用關鍵字*\[global values\]*(inherit \| initial \| revert \| revert-layer \| unset)幾乎每一個韓式皆可使用因以本表用法不將通用關鍵字寫入

[簡寫一覽](../abbreviationslist.md)

u: up
d: down
l: left
r: right

width \| height *\[size\]*: px,pt,%,em,ex,vw,vh,vmin,vmax
margin \| padding *\[size\]*: px,pt,%,em,vw,vh
font-size *\[size\]*: px,pt,pc,cm,mm,in,%,em,ex,rem,vw,vh,vmin,vmax
top \| bottom \| left \| right *\[size\]*: px,pt,%,em,ex,vw,vh
 *\[size\]*: px,pt,%,em,ex,vw,vh
 *\[size\]*: px,pt,%,em,ex,vw,vh


1. [css基本](../css.md)
2. [文字及段落]()
3. [背景]()
4. [容器及其副屬]()
5. [基本動畫]()
6. [清單及表單]()
7. [排版及定位]()
8. [display及基本排版]()
9. [網格系統](grid.md)
10. [偽元素]()
11. [偽類選擇器]()
12. [單位]()
13. [其他]()

小賀chris:) 2023/06/18 v1.2.6