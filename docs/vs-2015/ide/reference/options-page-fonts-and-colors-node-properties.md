---
title: Página de opciones, Propiedades de nodo Fuentes y colores | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- Tools Options settings, Fonts and Colors node properties
- automation [Visual Studio], controlling Tools Options
ms.assetid: 8e1ab784-5f85-4e2b-8ef9-e5d59ca4dbcb
caps.latest.revision: 12
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 23aa4eff3339ad3cd3ab7d4106745dc6fa83df34
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72662426"
---
# <a name="options-page-fonts-and-colors-node-properties"></a>Página de opciones, Propiedades de nodo Fuentes y colores
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

En este documento se describen las propiedades de fuente y color de una ventana de herramientas registrada para aparecer en **Fuentes y colores** en la categoría **Entorno** del cuadro de diálogo **Opciones**. Esto apoya la naturaleza dinámica de los grupos de elementos coloreables, que pueden cambiar si se instalan o desinstalan VSPackages.

 En la siguiente sección se muestran un ejemplo de un tipo de ventana registrada y las propiedades que están disponibles para cada ventana.

## <a name="text-editor-or-printer-or-dialogs-and-tool-windows"></a>Editor de texto o Impresora o Cuadros de diálogo y Ventanas de herramientas
 `DTE.Properties("FontsAndColors", "TextEditor")`

 O bien

 `DTE.Properties("FontsAndColors", "Printer")`

 O bien

 `DTE.Properties("FontsAndColors", "Dialogs and Tool Windows")`

|Nombre de elemento de propiedad|Valor|DESCRIPCIÓN|
|------------------------|-----------|-----------------|
|FontFamily|Get/Set (String)|Nombre de la fuente que se va a usar, por ejemplo, "Courier New".|
|FontCharacterSet|Get/Set (<xref:EnvDTE.vsFontCharSet>)|Valor <xref:EnvDTE.vsFontCharSet> que especifica el tipo de juego de caracteres que se va a usar, como hebreo o ruso.|
|FontSize|Get/Set (Short)|Tamaño de fuente que se va a usar, en puntos. Por ejemplo, 10 o 12.|

## <a name="see-also"></a>Otras referencias
 [Controlar la configuración](https://msdn.microsoft.com/library/a09ed242-7494-4cde-bbd1-7a8ec617965d) [de opciones determinar los nombres de elementos de propiedades en las páginas de opciones](https://msdn.microsoft.com/library/d450422d-47c7-4eeb-9f9f-3286264bc5aa) [Página opciones, página Opciones propiedades de nodo de entorno](../../ide/reference/options-page-environment-node-properties.md) [, propiedades del nodo editor de texto](../../ide/reference/options-page-text-editor-node-properties.md)
