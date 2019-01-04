---
title: Procedimiento Establecer comandos de implementación de SharePoint | Documentos de Microsoft
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, deploying
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 98aedc0c7fa557a45b43ab8344a49587b8febec1
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53920370"
---
# <a name="how-to-set-sharepoint-deployment-commands"></a>Procedimiento Establecer comandos de implementación de SharePoint
  Puede personalizar el proceso de implementación mediante el establecimiento de los comandos anteriores y posteriores a la implementación. Estos comandos se ejecutan antes y después de otras acciones de implementación al depurar soluciones de SharePoint en Visual Studio.  
  
### <a name="to-add-a-pre-deployment-command"></a>Para agregar un comando anterior a la implementación  
  
1.  En la barra de menús, elija **proyecto** > **\<*ProjectName*> propiedades**.  
  
2.  Elija la **SharePoint** ficha.  
  
3.  En el **línea de comandos anterior a la implementación** texto, escriba los comandos de MS-DOS o MSBuild para personalizar este paso.  
  
     Por ejemplo, para enumerar el contenido del directorio antes de que se completa la implementación, escriba **dir**.  
  
### <a name="to-add-a-post-deployment-command"></a>Para agregar un comando posterior a la implementación  
  
1.  En la barra de menús, elija **proyecto** > **\<*ProjectName*> propiedades**.  
  
2.  Elija la **SharePoint** ficha.  
  
3.  En el **implementación posterior a la línea de comandos** texto, escriba los comandos de MS-DOS o MSBuild para personalizar este paso.  
  
     Por ejemplo, para enumerar el contenido del directorio, una vez completada la implementación, escriba **dir**. Para usar una variable de MSBuild para copiar el ensamblado desde el directorio de compilación, escriba **copiar $ (TargetPath) c:\DeploymentDirectory**.  
  
## <a name="see-also"></a>Vea también
 [Empaquetar e implementar soluciones de SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
