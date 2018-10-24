---
title: Página de opciones, Propiedades de nodo Fuentes y colores
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- Tools Options settings, Fonts and Colors node properties
- automation [Visual Studio], controlling Tools Options
ms.assetid: 8e1ab784-5f85-4e2b-8ef9-e5d59ca4dbcb
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 05724c81b9983414c4e0c86870b630e29c33ade3
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49926584"
---
# <a name="options-page-fonts-and-colors-node-properties"></a>Página de opciones, Propiedades de nodo Fuentes y colores
En este documento se describen las propiedades de fuente y color de una ventana de herramientas registrada para aparecer en **Fuentes y colores** en la categoría **Entorno** del cuadro de diálogo **Opciones**. Esto apoya la naturaleza dinámica de los grupos de elementos coloreables, que pueden cambiar si se instalan o desinstalan VSPackages.

 En la siguiente sección se muestran un ejemplo de un tipo de ventana registrada y las propiedades que están disponibles para cada ventana.

## <a name="text-editor-or-printer-or-dialogs-and-tool-windows"></a>Editor de texto o Impresora o Cuadros de diálogo y Ventanas de herramientas
 `DTE.Properties("FontsAndColors", "TextEditor")`

 O bien

 `DTE.Properties("FontsAndColors", "Printer")`

 O bien

 `DTE.Properties("FontsAndColors", "Dialogs and Tool Windows")`

|Nombre de elemento de propiedad|Valor|Descripción|
| - |-----------|-----------------|
|FontFamily|Get/Set (String)|Nombre de la fuente que se va a usar, por ejemplo, "Courier New".|
|FontCharacterSet|Get/Set (<xref:EnvDTE.vsFontCharSet>)|Valor <xref:EnvDTE.vsFontCharSet> que especifica el tipo de juego de caracteres que se va a usar, como hebreo o ruso.|
|FontSize|Get/Set (Short)|Tamaño de fuente que se va a usar, en puntos. Por ejemplo, 10 o 12.|

## <a name="see-also"></a>Vea también

- [Control de la configuración de opciones](http://msdn.microsoft.com/Library/a09ed242-7494-4cde-bbd1-7a8ec617965d)
- [Determinación de los nombres de los elementos de propiedades en las páginas de opciones](http://msdn.microsoft.com/Library/d450422d-47c7-4eeb-9f9f-3286264bc5aa)
- [Página de opciones, Propiedades de nodo Entorno](../../ide/reference/options-page-environment-node-properties.md)
- [Página de opciones, Propiedades de nodo Editor de texto](../../ide/reference/options-page-text-editor-node-properties.md)