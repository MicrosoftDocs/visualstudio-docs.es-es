---
title: Páginas de propiedades Depurar archivos de código fuente/Solución
description: Acceda a la página de propiedades Depurar archivos de código fuente en Visual Studio haciendo clic con el botón derecho en su solución desde el Explorador de soluciones y, después, seleccione Propiedades > Propiedades comunes.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.debug.options.FindSource
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
- SQL
helpviewer_keywords:
- Debug Source Files property page
- debugging [Visual Studio], specifying source and symbol files
- source files, specifying in debugger
- debugger, source files
ms.assetid: 0af11464-eeb1-4d0b-87a6-0cc96779afb1
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: be57355c8fc38758080ebde344db0b4224bc3df8
ms.sourcegitcommit: fcfd0fc7702a47c81832ea97cf721cca5173e930
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2020
ms.locfileid: "97728530"
---
# <a name="debug-source-files-common-properties-solution-property-pages-dialog-box"></a>Depurar archivos de código fuente, Propiedades comunes, Páginas de propiedades de Solución (Cuadro de diálogo)
Esta página de propiedades especifica si el depurador buscará archivos de código fuente al depurar la solución.

 Para obtener acceso a la página de propiedades **Depurar archivos de código fuente**, en el **Explorador de soluciones**, haga clic con el botón derecho en la Solución y, a continuación, seleccione **Propiedades** en el menú contextual. Expanda la carpeta **Propiedades comunes** y haga clic en la página **Depurar archivos de código fuente**.

 **Directorios que contienen código fuente** Contiene una lista de directorios en los que el depurador busca archivos de código fuente al depurar la solución. Los subdirectorios de los directorios especificados también se incluyen en la búsqueda.

 **No buscar los archivos de código fuente siguientes** Especifique los nombres de los archivos que no quiere que lea el depurador. Si el depurador encuentra uno de estos archivos en uno de los directorios especificados anteriormente, lo omitirá. Si aparece el cuadro de diálogo **Buscar código fuente** mientras está depurando y hace clic en **Cancelar**, el archivo que buscaba se agregará a dicha lista y el depurador no seguirá buscándolo.

## <a name="see-also"></a>Vea también

- [Seguridad del depurador](../debugger/debugger-security.md)
- [Configuración y preparación de la depuración](../debugger/debugger-settings-and-preparation.md)