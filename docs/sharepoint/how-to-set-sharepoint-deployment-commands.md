---
title: "Cómo: establecer comandos de implementación de SharePoint | Documentos de Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords: SharePoint development in Visual Studio, deploying
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 2f465deaaca406c28aab177434e72de9746fb101
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-set-sharepoint-deployment-commands"></a>Cómo: Establecer comandos de implementación de SharePoint
  Puede personalizar el proceso de implementación estableciendo comandos anteriores y posteriores a la implementación. Estos comandos se ejecutan antes y después de otras acciones de implementación al depurar soluciones de SharePoint en Visual Studio.  
  
### <a name="to-add-a-pre-deployment-command"></a>Para agregar un comando anterior a la implementación  
  
1.  En la barra de menús, elija **Proyecto**, *NombreDeProyecto***Propiedades**.  
  
2.  Elija la **SharePoint** ficha.  
  
3.  En el **línea de comandos anterior a la implementación** texto cuadro, escriba comandos de MS-DOS o MSBuild para personalizar este paso.  
  
     Por ejemplo, para enumerar el contenido del directorio antes de que se complete la implementación, escriba **dir**.  
  
### <a name="to-add-a-post-deployment-command"></a>Para agregar un comando posterior a la implementación  
  
1.  En la barra de menús, elija **Proyecto**, *NombreDeProyecto***Propiedades**.  
  
2.  Elija la **SharePoint** ficha.  
  
3.  En el **línea de comandos posterior a la implementación** texto cuadro, escriba comandos de MS-DOS o MSBuild para personalizar este paso.  
  
     Por ejemplo, para enumerar el contenido del directorio una vez completada la implementación, escriba **dir**. Para usar una variable de MSBuild para copiar el ensamblado desde el directorio de compilación, escriba **copiar $ (TargetPath) c:\DeploymentDirectory**.  
  
## <a name="see-also"></a>Vea también  
 [Empaquetar e implementar soluciones de SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
  