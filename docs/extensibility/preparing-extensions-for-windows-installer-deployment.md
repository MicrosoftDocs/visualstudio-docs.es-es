---
title: "Preparar las extensiones para la implementaci&#243;n de Windows Installer | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "msi de VSIX"
ms.assetid: 5ee2d1ba-478a-4cb7-898f-c3b4b2ee834e
caps.latest.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 15
---
# Preparar las extensiones para la implementaci&#243;n de Windows Installer
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

No puede utilizar un paquete de Windows Installer \(MSI\) para implementar un paquete VSIX. Sin embargo, puede extraer el contenido de un paquete VSIX para la implementación de MSI. Este documento muestra cómo preparar un proyecto cuya salida predeterminada es un paquete VSIX para su inclusión en un proyecto de instalación.  
  
## Preparación de un proyecto de extensión para la implementación de Windows Installer  
 Realice estos pasos en los nuevos proyectos de extensión antes de agregar un proyecto de instalación.  
  
#### Para preparar un proyecto de extensión para la implementación de Windows Installer  
  
1.  Crear un paquete VSPackage, componente MEF, elementos gráficos del Editor u otro tipo de proyecto de extensibilidad que incluye un manifiesto VSIX.  
  
2.  Abra el manifiesto de VSIX en el editor de código.  
  
3.  Establezca el elemento InstalledByMsi del manifiesto VSIX para `true`. Para obtener más información sobre el manifiesto VSIX, consulte [Referencia de esquema 2.0 extensión VSIX](../extensibility/vsix-extension-schema-2-0-reference.md).  
  
     Esto impide que el instalador VSIX intentando instalar el componente.  
  
4.  Haga clic en el proyecto en **el Explorador de soluciones** y haga clic en **propiedades**.  
  
5.  Seleccione el **VSIX** ficha.  
  
6.  Active la casilla de verificación **contenido de VSIX de copia en la siguiente ubicación** y escriba la ruta de acceso para que el proyecto de instalación recogerá los archivos.  
  
## Extraer los archivos de un paquete VSIX existente  
 Realice estos pasos para agregar el contenido de un paquete VSIX existente a un proyecto de instalación cuando no tiene los archivos de origen.  
  
#### Para extraer archivos de un paquete VSIX existente  
  
1.  Cambiar el nombre de la. Archivo VSIX que contiene la extensión de *nombre de archivo*.vsix para *nombre de archivo*zip.  
  
2.  Copie el contenido del archivo zip en un directorio.  
  
3.  Eliminar el archivo \[Content\_types\] .xml desde el directorio.  
  
4.  Edite el manifiesto VSIX, tal como se muestra en el procedimiento anterior.  
  
5.  Agregue los archivos restantes al proyecto de instalación.  
  
## Vea también  
 [Visual Studio Installer Deployment](http://msdn.microsoft.com/es-es/121be21b-b916-43e2-8f10-8b080516d2a0)   
 [Walkthrough: Creating a Custom Action](http://msdn.microsoft.com/es-es/4bd4b63a-2b91-431e-839c-5752443f0eaf)