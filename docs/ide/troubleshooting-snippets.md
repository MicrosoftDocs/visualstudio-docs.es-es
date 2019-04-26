---
title: Solución de problemas con fragmentos de código
ms.date: 11/04/2016
ms.topic: troubleshooting
helpviewer_keywords:
- IntelliSense Code Snippets, troubleshooting
- troubleshooting IntelliSense Code Snippets
- troubleshooting Visual Basic, IntelliSense Code Snippets
ms.assetid: 7b6dd40e-2f78-4b50-8e68-41fac1bcb81e
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9485147bbe386983aa5ee9c492607e12afb151c6
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62575987"
---
# <a name="troubleshoot-snippets"></a>Solución de problemas con fragmentos de código

Los problemas relacionados con los fragmentos de código de IntelliSense suelen deberse a dos cosas: un archivo de fragmento de código dañado o la presencia de contenido incorrecto en el archivo de fragmento de código.

## <a name="the-snippet-cannot-be-dragged-from-file-explorer-to-a-visual-studio-source-file"></a>El fragmento de código no se puede arrastrar del Explorador de archivos a un archivo de código fuente de Visual Studio

- El código XML del archivo de fragmento de código puede estar dañado. El **Editor XML** de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] puede detectar problemas en la estructura XML.

- Es posible que el archivo de fragmento de código no se ajuste al esquema del fragmento. El **Editor XML** de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] puede detectar problemas en la estructura XML.

## <a name="the-code-has-compiler-errors-that-are-not-highlighted"></a>El código tiene errores del compilador que no están resaltados

- Es posible que falte una referencia de proyecto. Examine la documentación del fragmento de código. Si la referencia no se encuentra en el equipo, debe instalarla. La inserción de un fragmento de código debería agregar al proyecto todas las referencias necesarias. Si al fragmento de código le falta la información de referencia, esto se puede notificar al creador del fragmento de código como un error.

- Es posible que una variable no esté definida. Las variables sin definir en un fragmento de código deben aparecer resaltadas. De lo contrario, esto se puede notificar al creador del fragmento de código como un error.

## <a name="see-also"></a>Vea también

- [Fragmentos de código](../ide/code-snippets.md)
