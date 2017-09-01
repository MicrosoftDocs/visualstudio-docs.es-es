---
title: Comentarios
author: asb3993
ms.author: amburns
ms.date: 04/14/2017
ms.topic: article
ms.assetid: 0FE5E929-1846-4F48-B5E3-70990FAF9504
ms.translationtype: HT
ms.sourcegitcommit: e2b7ff9126e1cc38ac2e58d6be339b656a024e7f
ms.openlocfilehash: cb44dc755721f6095c9a07ad3e6fec1f6849e149
ms.contentlocale: es-es
ms.lasthandoff: 08/11/2017

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

