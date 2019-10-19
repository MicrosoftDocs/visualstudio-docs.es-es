---
title: Solucionar problemas con fragmentos de código | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: troubleshooting
helpviewer_keywords:
- IntelliSense Code Snippets, troubleshooting
- troubleshooting IntelliSense Code Snippets
- troubleshooting Visual Basic, IntelliSense Code Snippets
ms.assetid: 7b6dd40e-2f78-4b50-8e68-41fac1bcb81e
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f73cb7ba59daf2f8ee957d95dee36bba59f87614
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72654782"
---
# <a name="troubleshooting-snippets"></a>Solucionar problemas con fragmentos de código
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Los problemas relacionados con los fragmentos de código de IntelliSense suelen deberse a dos cosas: un archivo de fragmento de código dañado o la presencia de contenido incorrecto en el archivo de fragmento de código.

## <a name="common-problems"></a>Problemas habituales

### <a name="the-snippet-cannot-be-dragged-from-file-explorer-to-a-visual-studio-source-file"></a>El fragmento de código no se puede arrastrar del Explorador de archivos a un archivo de código fuente de Visual Studio

- El código XML del archivo de fragmento de código puede estar dañado. El **Editor XML** de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] puede detectar problemas en la estructura XML.

- Es posible que el archivo de fragmento de código no se ajuste al esquema del fragmento. El **Editor XML** de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] puede detectar problemas en la estructura XML.

### <a name="the-code-has-compiler-errors-that-are-not-highlighted"></a>El código tiene errores del compilador que no están resaltados

- Es posible que falte una referencia de proyecto. Examine la documentación del fragmento de código. Si la referencia no se encuentra en el equipo, debe instalarla. La inserción de un fragmento de código debería agregar al proyecto todas las referencias necesarias. Si al fragmento de código le falta la información de referencia, esto se puede notificar al creador del fragmento de código como un error.

- Es posible que una variable no esté definida. Las variables sin definir en un fragmento de código deben aparecer resaltadas. De lo contrario, esto se puede notificar al creador del fragmento de código como un error.

## <a name="see-also"></a>Otras referencias
 [Fragmentos de código](../ide/code-snippets.md)
