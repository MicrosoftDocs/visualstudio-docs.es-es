---
title: "Preparar las extensiones para la implementación de Windows Installer | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: vsix msi
ms.assetid: 5ee2d1ba-478a-4cb7-898f-c3b4b2ee834e
caps.latest.revision: "15"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: b72fc46d64034ddc22e929fb1a1eff26115cce70
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="preparing-extensions-for-windows-installer-deployment"></a>Preparar las extensiones para la implementación de Windows Installer
No se puede usar un paquete de Windows Installer (MSI) para implementar un paquete VSIX. Sin embargo, puede extraer el contenido de un paquete VSIX para la implementación de MSI. Este documento muestra cómo preparar un proyecto cuyo resultado predeterminado es un paquete VSIX para su inclusión en un proyecto de instalación.  
  
## <a name="preparing-an-extension-project-for-windows-installer-deployment"></a>Preparar un proyecto de extensión para la implementación de Windows Installer  
 Realice estos pasos en los nuevos proyectos de extensión antes de agregar a un proyecto de instalación.  
  
#### <a name="to-prepare-an-extension-project-for-windows-installer-deployment"></a>Para preparar un proyecto de extensión para la implementación de Windows Installer  
  
1.  Crear un paquete VSPackage, componente MEF, elementos gráficos del Editor u otro tipo de proyecto de extensibilidad que incluya un manifiesto VSIX.  
  
2.  Abra el manifiesto de VSIX en el editor de código.  
  
3.  Establezca el elemento InstalledByMsi del manifiesto VSIX para `true`. Para obtener más información sobre el manifiesto de VSIX, vea [VSIX extensión de esquema 2.0 referencia](../extensibility/vsix-extension-schema-2-0-reference.md).  
  
     Esto impide que al instalador VSIX al intentar instalar el componente.  
  
4.  Haga clic en el proyecto en **el Explorador de soluciones** y haga clic en **propiedades**.  
  
5.  Seleccione el **VSIX** ficha.  
  
6.  Active la casilla de verificación **contenido de VSIX de copia en la siguiente ubicación** y escriba la ruta de acceso en el proyecto de instalación recogerá los archivos.  
  
## <a name="extracting-files-from-an-existing-vsix-package"></a>Extraer los archivos de un paquete VSIX existente  
 Siga estos pasos para agregar el contenido de un paquete VSIX existente a un proyecto de instalación cuando no tiene los archivos de origen.  
  
#### <a name="to-extract-files-from-an-existing-vsix-package"></a>Para extraer los archivos de un paquete VSIX existente  
  
1.  Cambiar el nombre de la. Archivo VSIX que contiene la extensión de *filename*.vsix a *filename*zip.  
  
2.  Copie el contenido del archivo zip en un directorio.  
  
3.  Eliminar el archivo [Content_types] .xml desde el directorio.  
  
4.  Edite el manifiesto VSIX, tal como se muestra en el procedimiento anterior.  
  
5.  Agregue los archivos restantes al proyecto de instalación.  
  
## <a name="see-also"></a>Vea también  
 [Implementación del instalador de Visual Studio](http://msdn.microsoft.com/en-us/121be21b-b916-43e2-8f10-8b080516d2a0)   
 [Tutorial: Crear una acción personalizada](http://msdn.microsoft.com/en-us/4bd4b63a-2b91-431e-839c-5752443f0eaf)