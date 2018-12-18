---
title: 'Cómo: crear un paquete de solución de SharePoint mediante el uso de las tareas de MSBuild | Microsoft Docs'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, packages
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 5a95eb80b860a1447fe6e958edb9c98b66805a90
ms.sourcegitcommit: d9e4ea95d0ea70827de281754067309a517205a1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/29/2018
ms.locfileid: "37119371"
---
# <a name="how-to-create-a-sharepoint-solution-package-by-using-msbuild-tasks"></a>Cómo: crear un paquete de solución de SharePoint mediante el uso de las tareas de MSBuild
  Puede compilar, limpiar y validar un paquete de SharePoint (*.wsp*) con las tareas de MSBuild de línea de comandos en un equipo de desarrollo. También puede usar estos comandos para automatizar el proceso de compilación mediante Team Foundation Server en un equipo de compilación.  
  
## <a name="build-a-sharepoint-package"></a>Crear un paquete de SharePoint  
  
#### <a name="to-build-a-sharepoint-package"></a>Para compilar un paquete de SharePoint  
  
1.  En el Windows **iniciar** menú, elija **todos los programas** > **Accesorios** > **símbolo**.  
  
2.  Cambie al directorio donde se encuentra el proyecto de SharePoint.  
  
3.  Escriba el siguiente comando para crear un paquete para el proyecto. Reemplace *ProjectFileName* con el nombre del proyecto.  
  
    ```cmd  
    msbuild /t:Package ProjectFileName  
    ```  
  
     Por ejemplo, podría ejecutar uno de los siguientes comandos para empaquetar un proyecto de SharePoint denominado ListDefinition1.  
  
    ```cmd  
    msbuild /t:Package ListDefinition1.vbproj  
    msbuild /t:Package ListDefinition1.csproj  
    ```  
  
## <a name="clean-a-sharepoint-package"></a>Limpiar un paquete de SharePoint  
  
#### <a name="to-clean-a-sharepoint-package"></a>Para limpiar un paquete de SharePoint  
  
1.  Abra una ventana de símbolo del sistema.  
  
2.  Cambie al directorio donde se encuentra el proyecto de SharePoint.  
  
3.  Escriba el siguiente comando para limpiar un paquete para el proyecto. Reemplace *ProjectFileName* con el nombre del proyecto.  
  
    ```cmd  
    msbuild /t:CleanPackage ProjectFileName  
    ```  
  
     Por ejemplo, podría ejecutar uno de los comandos siguientes para limpiar un proyecto de SharePoint denominado ListDefinition1.  
  
    ```cmd  
    msbuild /t:CleanPackage ListDefinition1.vbproj  
    msbuild /t:CleanPackage ListDefinition1.csproj  
    ```  
  
## <a name="validate-a-sharepoint-package"></a>Validar un paquete de SharePoint  
  
#### <a name="to-validate-a-sharepoint-package"></a>Para validar un paquete de SharePoint  
  
1.  Abra una ventana de símbolo del sistema.  
  
2.  Cambie al directorio donde se encuentra el proyecto de SharePoint.  
  
3.  Escriba el siguiente comando para validar un paquete para el proyecto. Reemplace *ProjectFileName* con el nombre del proyecto.  
  
    ```cmd  
    msbuild /t:ValidatePackage ProjectFileName  
    ```  
  
     Por ejemplo, podría ejecutar uno de los comandos siguientes para validar un proyecto de SharePoint denominado ListDefinition1.  
  
    ```cmd  
    msbuild /t:ValidatePackage ListDefinition1.vbproj  
    msbuild /t:ValidatePackage ListDefinition1.csproj  
    ```  
  
## <a name="set-properties-in-a-sharepoint-package"></a>Establecer propiedades en un paquete de SharePoint  
  
#### <a name="to-set-a-property-in-a-sharepoint-package"></a>Para establecer una propiedad en un paquete de SharePoint  
  
1.  Abra una ventana de símbolo del sistema.  
  
2.  Cambie al directorio donde se encuentra el proyecto de SharePoint.  
  
3.  Escriba el siguiente comando para establecer una propiedad en un paquete para el proyecto. Reemplace *PropertyName* con la propiedad que desea establecer.  
  
    ```cmd  
    msbuild /property:PropertyName=Value  
    ```  
  
     Por ejemplo, podría ejecutar el comando siguiente para establecer el nivel de advertencia.  
  
    ```cmd  
    msbuild /property:WarningLevel = 2  
    ```  
  
## <a name="see-also"></a>Vea también
 [Crear características de SharePoint](../sharepoint/creating-sharepoint-features.md)   
 [Cómo: personalizar una característica de SharePoint](../sharepoint/how-to-customize-a-sharepoint-feature.md)   
 [Cómo: agregar y quitar elementos de las características de SharePoint](../sharepoint/how-to-add-and-remove-items-to-sharepoint-features.md)  
