---
title: "C&#243;mo: Crear un paquete de soluci&#243;n de SharePoint con las tareas de MSBuild | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "desarrollo de SharePoint en Visual Studio, paquetes"
ms.assetid: c3880bdd-f0a1-4d53-9a97-5767cb3f7b8e
caps.latest.revision: 17
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 16
---
# C&#243;mo: Crear un paquete de soluci&#243;n de SharePoint con las tareas de MSBuild
  Puede compilar, limpiar y validar un paquete de SharePoint \(.wsp\) usando las tareas de MSBuild de la línea de comandos en un equipo de desarrollo.  También puede utilizar estos comandos para automatizar el proceso de compilación utilizando Team Foundation Server en un equipo de compilación.  
  
## Compilar un paquete de SharePoint  
  
#### Para compilar un paquete de SharePoint  
  
1.  En el menú de Windows **Comienzo** , elija **Todos los programas**, **Accesorios**, **Símbolo del sistema**.  
  
2.  Cambie al directorio donde se encuentra el proyecto de SharePoint.  
  
3.  Escriba el comando siguiente para crear un paquete para el proyecto.  Reemplace *ProjectFileName* con el nombre del proyecto.  
  
    ```  
    msbuild /t:Package ProjectFileName  
    ```  
  
     Por ejemplo, podría ejecutar uno de los comandos siguientes para empaquetar un proyecto de SharePoint denominado ListDefinition1.  
  
    ```  
    msbuild /t:Package ListDefinition1.vbproj  
    msbuild /t:Package ListDefinition1.csproj  
    ```  
  
## Limpiar un paquete de SharePoint  
  
#### Para limpiar un paquete de SharePoint  
  
1.  Abra una ventana de símbolo del sistema.  
  
2.  Cambie al directorio donde se encuentra el proyecto de SharePoint.  
  
3.  Escriba el comando siguiente para limpiar un paquete del proyecto.  Reemplace *ProjectFileName* con el nombre del proyecto.  
  
    ```  
    msbuild /t:CleanPackage ProjectFileName  
    ```  
  
     Por ejemplo, podría ejecutar uno de los comandos siguientes para limpiar un proyecto de SharePoint denominado ListDefinition1.  
  
    ```  
    msbuild /t:CleanPackage ListDefinition1.vbproj  
    msbuild /t:CleanPackage ListDefinition1.csproj  
    ```  
  
## Validar un paquete de SharePoint  
  
#### Para validar un paquete de SharePoint  
  
1.  Abra una ventana de símbolo del sistema.  
  
2.  Cambie al directorio donde se encuentra el proyecto de SharePoint.  
  
3.  Escriba el comando siguiente para validar un paquete para el proyecto.  Reemplace *ProjectFileName* con el nombre del proyecto.  
  
    ```  
    msbuild /t:ValidatePackage ProjectFileName  
    ```  
  
     Por ejemplo, podría ejecutar uno de los comandos siguientes para validar un proyecto de SharePoint denominado ListDefinition1.  
  
    ```  
    msbuild /t:ValidatePackage ListDefinition1.vbproj  
    msbuild /t:ValidatePackage ListDefinition1.csproj  
    ```  
  
## Establecer propiedades en un paquete de SharePoint  
  
#### Para establecer una propiedad en un paquete de SharePoint  
  
1.  Abra una ventana de símbolo del sistema.  
  
2.  Cambie al directorio donde se encuentra el proyecto de SharePoint.  
  
3.  Escriba el comando siguiente para establecer una propiedad en un paquete para el proyecto.  Reemplace *PropertyName* con la propiedad que desea establecer.  
  
    ```  
    msbuild /property:PropertyName=Value  
    ```  
  
     Por ejemplo, podría ejecutar el comando siguiente para establecer el nivel de advertencia.  
  
    ```  
    msbuild /property:WarningLevel = 2  
    ```  
  
## Vea también  
 [Crear características de SharePoint](../sharepoint/creating-sharepoint-features.md)   
 [Cómo: Personalizar una característica de SharePoint](../sharepoint/how-to-customize-a-sharepoint-feature.md)   
 [Cómo: Agregar y quitar elementos de las características de SharePoint](../sharepoint/how-to-add-and-remove-items-to-sharepoint-features.md)  
  
  