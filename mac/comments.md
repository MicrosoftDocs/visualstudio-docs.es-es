---
title: Comentarios
description: En este artículo se describe la utilización de comentarios en el editor de código fuente de Visual Studio para Mac
author: asb3993
ms.author: amburns
ms.date: 05/06/2018
ms.assetid: 0FE5E929-1846-4F48-B5E3-70990FAF9504
ms.openlocfilehash: 4a7dfd0daaddad9f91d461689a0174469dd253c2
ms.sourcegitcommit: 33c954fbc8e05f7ba54bfa2c0d1bc1f9bbc68876
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2018
ms.locfileid: "33865392"
---
# <a name="comments"></a>Comentarios

Al depurar o experimentar con código, puede ser útil comentar bloques de código de forma temporal o a largo plazo. 

Para comentar un bloque de código completo:

* Seleccione el código y **Alternar comentario de línea** en el menú contextual

O

* Use el enlace de teclado `cmd + /` en el código seleccionado.

Estos métodos se pueden usar para comentar secciones de código y quitar los comentarios de ellas. En archivos de C# se pueden agregar niveles adicionales de comentarios de línea, lo que permite comentar regiones de códigos y quitar los comentarios sin perder los comentarios reales: 

 ![comentarios de varios niveles](media/source-editor-image8.png)

Los comentarios también son útiles para documentar el código para los desarrolladores futuros que puedan interactuar con él. Normalmente se realizan en el formato de comentarios de varias líneas, que se agregan de la manera siguiente en cada lenguaje:

**C#**

``` cs
/*
 This is a multi-line
 comment in C#
*/
```
**F#**

```fsharp
(*
 This is a multi-line
  comment in F#
*)
```
