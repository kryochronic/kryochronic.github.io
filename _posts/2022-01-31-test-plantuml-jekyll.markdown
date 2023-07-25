---
layout: post
title:  "Examples of PlantUML WBS"
date:   2022-01-31 23:47:00 +0530
categories: jekyll plantuml wbs sample code
---

# Examples of PlantUML WBS
The diagram below is an example of a simple WBS(source [here](https://gist.githubusercontent.com/kryochronic/0e891d36b112f324025355cf32fd3c69/raw/6446444dd3189f3ac6cdfad993694b414140652e/sample_sprint_wbs.puml)).

```plantuml

@startwbs SprintGoalsExample
scale 0.5
' skinparam Monochrome reverse
skinparam HorizontalAlignment left
skinparam Padding 3
skinparam WrapWidth 20

' !include https://gist.githubusercontent.com/kryochronic/2f2fa8bd421e4729fb90e8685afcc90c/raw/5a0433838d4ea103b303439797e09c43e0cda814/wbs-styles.puml
!include https://gist.githubusercontent.com/kryochronic/0e891d36b112f324025355cf32fd3c69/raw/4b471b791435dcdd17e1819de408a5a710908f5c/sample_sprint_wbs.puml
@endwbs

```

---

## Under the hood, advacnced PlantUML ...

### Add some styling

```text
@startwbs SprintGoalsExample
' skinparam Monochrome reverse
skinparam HorizontalAlignment left
skinparam Padding 3
skinparam WrapWidth 20

!include https://gist.githubusercontent.com/kryochronic/2f2fa8bd421e4729fb90e8685afcc90c/raw/5a0433838d4ea103b303439797e09c43e0cda814/wbs-styles.puml
!include https://gist.githubusercontent.com/kryochronic/0e891d36b112f324025355cf32fd3c69/raw/4b471b791435dcdd17e1819de408a5a710908f5c/sample_sprint_wbs.puml
@endwbs

```

will result in a diagram like the following

```plantuml

@startwbs SprintGoalsExample
scale 0.5
' skinparam Monochrome reverse
skinparam HorizontalAlignment left
skinparam Padding 3
skinparam WrapWidth 20

!include https://gist.githubusercontent.com/kryochronic/2f2fa8bd421e4729fb90e8685afcc90c/raw/5a0433838d4ea103b303439797e09c43e0cda814/wbs-styles.puml
!include https://gist.githubusercontent.com/kryochronic/0e891d36b112f324025355cf32fd3c69/raw/4b471b791435dcdd17e1819de408a5a710908f5c/sample_sprint_wbs.puml
@endwbs

```

---

### Mixing Icons & Text

:question: Did you notice the `Person Icon` preceding the name(s) in the Pod Member Names above ?

:sunglasses: You can use icons by placing a `<&icon-name{scale=1.5}>` where `icon-name` is an icon name from [useiconic.com](https:/https://useiconic.com/open).
Icon Sizes can be adjusted with a `scale` key-value pair, as shown above.

### PlantUML Variables

The syntax below defines a `string` variable, with the name `$N_JA`.
```
!$N_JA = "<&person{scale=1.5}> **SomeName 00**"
```

We can now use the variable in the diagram.

```plantuml
!$N_JA = "<&person{scale=1.5}> **SomeName 00**"
title 
the variable **<math>N_JA</math>** is rendered as $N_JA when derefereced with a <math>$</math>.
end title
```

---

### More Styling

The above is justone of the types of document that can be created using PlantUML.

#### Themes

##### aws-orange

A `aws-orange` themed output:


```text
@startwbs
!theme aws-orange
!include https://gist.githubusercontent.com/kryochronic/0e891d36b112f324025355cf32fd3c69/raw/4b471b791435dcdd17e1819de408a5a710908f5c/sample_sprint_wbs.puml
@endwbs
```

```plantuml
@startwbs
!theme aws-orange
!include https://gist.githubusercontent.com/kryochronic/0e891d36b112f324025355cf32fd3c69/raw/4b471b791435dcdd17e1819de408a5a710908f5c/sample_sprint_wbs.puml
@endwbs
```

---


##### blueprint

A `blueprint` themed output(My Favourite):

```text
@startwbs
!theme blueprint
!include https://gist.githubusercontent.com/kryochronic/0e891d36b112f324025355cf32fd3c69/raw/4b471b791435dcdd17e1819de408a5a710908f5c/sample_sprint_wbs.puml
@endwbs
```

```plantuml
@startwbs
!theme blueprint
!include https://gist.githubusercontent.com/kryochronic/0e891d36b112f324025355cf32fd3c69/raw/4b471b791435dcdd17e1819de408a5a710908f5c/sample_sprint_wbs.puml
@endwbs
```
---