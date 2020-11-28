---
title: 'Cómo: establecer comandos de implementación de SharePoint | Microsoft Docs'
description: Aprenda a personalizar el proceso de implementación mediante el establecimiento de comandos previos y posteriores a la implementación de SharePoint.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, deploying
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: fc1da67206e5e5c9fde1b5c595424239d1685ac7
ms.sourcegitcommit: 2244665d5a0e22d12dd976417f2a782e68684705
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/28/2020
ms.locfileid: "96304390"
---
# <a name="how-to-set-sharepoint-deployment-commands"></a>Cómo: establecer comandos de implementación de SharePoint
  Puede personalizar el proceso de implementación mediante el establecimiento de comandos previos y posteriores a la implementación. Estos comandos se ejecutan antes y después de otras acciones de implementación al depurar soluciones de SharePoint desde Visual Studio.

### <a name="to-add-a-pre-deployment-command"></a>Para agregar un comando anterior a la implementación

1. En la barra de menús, **Project** elija  >  **\<*ProjectName*> propiedades** del proyecto.

2. Elija la pestaña **SharePoint** .

3. En el cuadro de texto **línea de comandos anterior a la implementación** , escriba los comandos MS-dos o MSBuild para personalizar este paso.

     Por ejemplo, para mostrar el contenido del directorio antes de que se complete la implementación, escriba **dir**.

### <a name="to-add-a-post-deployment-command"></a>Para agregar un comando posterior a la implementación

1. En la barra de menús, **Project** elija  >  **\<*ProjectName*> propiedades** del proyecto.

2. Elija la pestaña **SharePoint** .

3. En el cuadro de texto **línea de comandos posterior a la implementación** , escriba los comandos MS-dos o MSBuild para personalizar este paso.

     Por ejemplo, para mostrar el contenido del directorio una vez completada la implementación, escriba **dir**. Para usar una variable de MSBuild para copiar el ensamblado desde el directorio de compilación, escriba **Copy $ (TargetPath) c:\DeploymentDirectory**.

## <a name="see-also"></a>Consulte también
- [Empaquetado e implementación de soluciones de SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
