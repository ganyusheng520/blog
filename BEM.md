### 前言


>BEM命名规范无疑是优秀的，它能够防止你的CSS代码陷入混乱,难以维护。当我刚接触到BEM的时候，我一下子就喜欢上了这种规范，下面我将给大家分享下。    

CSS是一门易于书写并容易理解的语言，但如果要在一个大型的项目中保持你的CSS代码整洁，易于维护却不是一件容易的事情，很多人往往把它写的杂乱无章。很多时候，你需要理解某部分代码时，你可能需要从头开始读起。这种场景是不是似曾相似呢？也许这个时候就需要一套规范让大家共同遵守了。常见的规范很多，每个人的选择可能也不一样，而我则选择使用BEM命名规范

![来源: Mat Przegiętka](https://user-gold-cdn.xitu.io/2017/11/27/15ffdbb21dc20cb9?w=2000&h=1200&f=png&s=51522)

图片来源：<a href="https://dribbble.com/MatPrzegietka?utm_source=Medium&utm_medium=link&utm_campaign=BEM"> Mat Przegiętka</a>


### BEM是什么？


BEM是一种CSS类命名规范，通过 **模块化** 和 **可维护** 的方式 **编写样式**。

BEM是 **块（Block），元素（Element），修饰符（Modifier）**的缩写。

例如：'block__element--modifier'

类的命名总是以块名开始,然后是元素名（可选，前面加两个下划线），最后是修饰符（也可选，前面加两个破折号）。

![图1：在BEM中命名的组件示例](https://user-gold-cdn.xitu.io/2017/11/27/15ffdbb21cc8e7dd?w=1195&h=457&f=png&s=71078)

### 块(Block)

块是一个独立的，可重复使用的模块 , 你可以将其视为前端框架中的**组件**。例如，一个上图示例的"card"就是一个很典型的块。 


*注意：避免使用特定内容的命名（比如“shopping-list”）,推荐使用通用的名称（比如“check-list”），以便在不同的场景中复用它们（“check-list”和“todo-list”）。*


### 元素(Element)

元素是只存在于其块内的**子**元素。

比如上图示例中的`card__title,card__text` 或 `card__button`。


*注意：元素嵌套只能有一个层级，所以`card__button__text`是不可行的。你应该定义另一个名为“button”的块（由`button__text`组成）。*

### 修饰符(Modifier)


修饰符可以为块或元素提供额外的描述，如颜色，状态等。

通过这种方式，我们可以有像`card__button--primary`这样的`card--featured`类。

*注意：修饰符只能进行修饰，并总是伴随着基础块。对于card，它将是：“card card--featured”，其中基础块定义了内边距和边框，而修饰符则定义了背景颜色。*

![图2：修饰符示例](https://user-gold-cdn.xitu.io/2017/11/27/15ffe245e873d65c?w=1100&h=433&f=png&s=50803)

* 除了BEM三个核心部分，你还可以给类添加 <a href="https://csswizardry.com/2015/03/more-transparent-ui-code-with-namespaces/">命名空间</a> **前缀**。

想深入理解可点击 <a href="http://getbem.com/naming/">getbem</a> 和 <a href="https://en.bem.info/methodology/naming-convention/">Naming convention</a> 。此外，还有一些 <a href="https://www.smashingmagazine.com/2016/06/battling-bem-extended-edition-common-problems-and-how-to-avoid-them/">相关博文</a>。


### BEM 有哪些优势

**广泛认可**

BEM是**最受开发者认可**的命名规范之一。也就是说，当你为你的BEM项目引入新的开发成员时，他们很有可能已经了解过这一规范，从而**缩短了学习和适应的过程**，从而让他们**快速投入开发**。

**可读性强**

每个元素都有语义化的类名，这样CSS样式表可读性非常强。选择器不仅阅读起来更舒适，也比多层嵌套的写法运行效率更高。

![图3：语义化的BEM命名 VS 标签选择器](https://user-gold-cdn.xitu.io/2017/11/27/15ffe245e7fe9f7d?w=1100&h=383&f=png&s=16365)

**扩展性强**

CSS选择器的粒度足够地细，改动时就变得非常简单。只需要修改一个选择器就够了，也不用担心两个选择器之间产生的权重问题

![图4：重写二级菜单图标的样式（BEM与嵌套标签）](https://user-gold-cdn.xitu.io/2017/11/27/15ffe245ee4ed6c0?w=1100&h=392&f=png&s=22447)

**适应性强**

模块化复用的理念，让BEM很容易配合其他框架一起使用。 此外，样式与元素类型和嵌套无关，不会打乱文档结构。

![图5：元素类型和嵌套的重要性（BEM与标签））](https://user-gold-cdn.xitu.io/2017/11/27/15ffe245e7497e02?w=1100&h=455&f=png&s=42501)

**健壮性**

>计算机科学只有两件事难以处理：缓存失效和命名。
>—— Phil Karlton

当你开始使用BEM时，你可能会发现自己会有许多**疑虑**。 
这反而是一件**好事**:

1. 使用合适的块**命名**让你的代码**清晰易读**，别人更容易理解（也包括你以后自己理解）

2. **相似**的模块推荐**复用**已有的类名

3. 避免多级**嵌套**


简而言之，它会**促使**你开始注意细节，思考问题，从而**提高代码的质量**。 准备好使用BEM了吗？

译者：由于本人水平有限，翻译的内容难免有错漏和理解偏差之处，欢迎各位大神指正

原文：https://blog.elpassion.com/reasons-to-use-bem-a88738317753

