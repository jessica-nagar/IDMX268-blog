---
template: blog-post
title: Everything you need to know to get started with Cascade Layers
slug: /article-1
date: 2022-02-06 21:45
description: Everything you need to know to get started with Cascade Layers
featuredImage: /assets/fredrick-tendong-hvyepjyehdq-unsplash.jpg
---
**Basic Knowledge**

            Cascade layers is a new and important part of determining what style will actually be applied to web page. The @layer rule allows explicit orchestration of how styles from different sources are evaluated and prioritized. The purpose of cascade layers can be understood by understanding a foundational principle of the cascade: origins. When browsers composite styles, there are three primary origins: Author (the stylesheets you add to your website), User origins (style the browsers may allow providing as preferences such as default font, font size, and color), User-agent (default styles applied by the browser.) Due to the "virtual" rules they create, transitions and animations are considered origins. CSS uses the !important rule to add more importance to a property or value than usual. This rule also revers the order of origins when used, meaning instead of the order being: author, user, user-agent, it would be, user-agent, user, author.

            The browser applies the style based on the cascade sort order. The sort order before cascade layers were introduced was: origins of importance, context (inside a shadow DOM), element (attached styles, within the style attribute), specificity, and order of appearance (aka, the last one “wins”.) The new cascade layer rule will be placed in between element and specificity making it higher priority then specificity and order of appearance.

 

 

**Use Cases for Cascade Layers**

            One way to use Cascade Layers is to layer everything so priority of the levels are clear. Also you can use unlayered CSS as powerful overrides because they will always out weight layered CSS. We can make resets the lowest layer because we want the other code to take priority over them. Make any third party code parts of the middle layers, because we want to use them but we want our code to be the main focus. So on that note we should make anything that the author or team wrote as the highest level because it is the style we most likely want to see since we are setting it up the way we intend it to be seen,

            The use of resets or baseline styles can smooth out browser inconsistencies for common elements or provide sensible defaults based on the expected application. These styles are usually intended to have the lowest priority, so they should be listed as your first layer. In addition, since these styles are in layers, they can be amended or added to later.

            Framework and library overrides are primarily used for preset styles. Writers try to keep specificity low and offer customization methods. Utilizing layers, you can area the framework in its own layer to demote it to the lowest specificity.

**Defining Cascade Layers and Specificity**

            @layers is a new rule that applies to cascade layers. The sequence of layers matters because layers change the game in terms of specificity, which is the first key notion of using @layers. Layers have the advantage of being able to have their order defined first, and then styles added later. Using the @layer rule and a name to create a block for the layer styles is one technique to define a layer. Another way to define layers, is to use the @layer statement, and structure it as a multi- or single-line statement. This feature is useful since it allows authors to declare the layer order in a single place at the top of their styles. Add styles later via the block or import them by using the same name later

You can also nest @layer rules. Then to add onto nested rules later, you reference the parent and nested rules together using dot notation. Alternatively, you can define nested layers up-front using dot notation. If you reuse a name within a nested layer, it will not reference the outer layer but start a new layer with that name. Naming is optional, but the downside is you cannot add to them later, and whenever they are added determines their priority.

The first part of specificity for layers is order. Layers defined later will have their rules take priority over layers defined earlier. A more simple selector in a later layer can override what historically would have been a stronger selector in an earlier layer. Unlayered styles would always take the highest priority. Styles outside of layer will ultimately “win” over styles within layers. Unlayered styles have priority even if they are ordered before any layers are defined. If you write styles inside a layer and then add nested layers, the rules outside of nested layers act like unlayered styles in terms of cascade specificity. So if your nested layers have the potential to override each other, you may want to insure all styles with the parent layer themselves are within layers.