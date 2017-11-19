---
title: "Cómo: crear un paquete de solución de SharePoint con las tareas de MSBuild | Documentos de Microsoft"
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
helpviewer_keywords: SharePoint development in Visual Studio, packages
ms.assetid: c3880bdd-f0a1-4d53-9a97-5767cb3f7b8e
caps.latest.revision: "17"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 3cfe26fde4dd2d2b6617a008769fd535bb3e2cbb
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-create-a-sharepoint-solution-package-by-using-msbuild-tasks"></a>Cómo: Crear un paquete de solución de SharePoint con las tareas de MSBuild
  Puede compilar, limpiar y validar un paquete de SharePoint (.wsp) mediante tareas de MSBuild de línea de comandos en un equipo de desarrollo. También puede usar estos comandos para automatizar el proceso de compilación mediante Team Foundation Server en un equipo de compilación.  
  
## <a name="building-a-sharepoint-package"></a>Compilar un paquete de SharePoint  
  
#### <a name="to-build-a-sharepoint-package"></a>Para crear un paquete de SharePoint  
  
1.  En las ventanas **iniciar** menú, elija **todos los programas**, **Accesorios**, **símbolo**.  
  
2.  Cambie al directorio donde se encuentra el proyecto de SharePoint.  
  
3.  Escriba el siguiente comando para crear un paquete para el proyecto. Reemplace *ProjectFileName* con el nombre del proyecto.  
  
    ```  
    msbuild /t:Package ProjectFileName  
    ```  
  
     Por ejemplo, podría ejecutar uno de los siguientes comandos para empaquetar un proyecto de SharePoint denominado ListDefinition1.  
  
    ```  
    msbuild /t:Package ListDefinition1.vbproj  
    msbuild /t:Package ListDefinition1.csproj  
    ```  
  
## <a name="cleaning-a-sharepoint-package"></a>Limpiar un paquete de SharePoint  
  
#### <a name="to-clean-a-sharepoint-package"></a>Para limpiar un paquete de SharePoint  
  
1.  Abra una ventana de símbolo del sistema.  
  
2.  Cambie al directorio donde se encuentra el proyecto de SharePoint.  
  
3.  Escriba el siguiente comando para limpiar un paquete para el proyecto. Reemplace *ProjectFileName* con el nombre del proyecto.  
  
    ```  
    msbuild /t:CleanPackage ProjectFileName  
    ```  
  
     Por ejemplo, podría ejecutar uno de los comandos siguientes para limpiar un proyecto de SharePoint denominado ListDefinition1.  
  
    ```  
    msbuild /t:CleanPackage ListDefinition1.vbproj  
    msbuild /t:CleanPackage ListDefinition1.csproj  
    ```  
  
## <a name="validating-a-sharepoint-package"></a>Validar un paquete de SharePoint  
  
#### <a name="to-validate-a-sharepoint-package"></a>Para validar un paquete de SharePoint  
  
1.  Abra una ventana de símbolo del sistema.  
  
2.  Cambie al directorio donde se encuentra el proyecto de SharePoint.  
  
3.  Escriba el siguiente comando para validar un paquete para el proyecto. Reemplace *ProjectFileName* con el nombre del proyecto.  
  
    ```  
    msbuild /t:ValidatePackage ProjectFileName  
    ```  
  
     Por ejemplo, podría ejecutar uno de los comandos siguientes para validar un proyecto de SharePoint denominado ListDefinition1.  
  
    ```  
    msbuild /t:ValidatePackage ListDefinition1.vbproj  
    msbuild /t:ValidatePackage ListDefinition1.csproj  
    ```  
  
## <a name="setting-properties-in-a-sharepoint-package"></a>Establecer las propiedades en un paquete de SharePoint  
  
#### <a name="to-set-a-property-in-a-sharepoint-package"></a>Para establecer una propiedad en un paquete de SharePoint  
  
1.  Abra una ventana de símbolo del sistema.  
  
2.  Cambie al directorio donde se encuentra el proyecto de SharePoint.  
  
3.  Escriba el siguiente comando para establecer una propiedad en un paquete para el proyecto. Reemplace *PropertyName* con la propiedad que desea establecer.  
  
    ```  
    msbuild /property:PropertyName=Value  
    ```  
  
     Por ejemplo, podría ejecutar el comando siguiente para establecer el nivel de advertencia.  
  
    ```  
    msbuild /property:WarningLevel = 2  
    ```  
  
## <a name="see-also"></a>Vea también  
 [Crear características de SharePoint](../sharepoint/creating-sharepoint-features.md)   
 [Cómo: personalizar una característica de SharePoint](../sharepoint/how-to-customize-a-sharepoint-feature.md)   
 [Cómo: Agregar y quitar elementos de las características de SharePoint](../sharepoint/how-to-add-and-remove-items-to-sharepoint-features.md)  
  
  