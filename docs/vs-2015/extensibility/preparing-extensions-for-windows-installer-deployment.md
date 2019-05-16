---
title: Preparación de las extensiones para la implementación de Windows Installer | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- vsix msi
ms.assetid: 5ee2d1ba-478a-4cb7-898f-c3b4b2ee834e
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 76d7f879fade99914bf3f56ade0ec1270e14f4c7
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/15/2019
ms.locfileid: "65694595"
---
# <a name="preparing-extensions-for-windows-installer-deployment"></a>Preparación de las extensiones para la implementación de Windows Installer
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

No se puede usar un paquete de Windows Installer (MSI) para implementar un paquete VSIX. Sin embargo, puede extraer el contenido de un paquete VSIX para la implementación de MSI. Este documento muestra cómo preparar un proyecto cuya salida predeterminada es un paquete VSIX para su inclusión en un proyecto de instalación.  
  
## <a name="preparing-an-extension-project-for-windows-installer-deployment"></a>Preparación de un proyecto de extensión para la implementación de Windows Installer  
 Realice estos pasos en nuevos proyectos de extensión antes de agregar a un proyecto de instalación.  
  
#### <a name="to-prepare-an-extension-project-for-windows-installer-deployment"></a>Para preparar un proyecto de extensión para la implementación de Windows Installer  
  
1. Crear un VSPackage, el componente MEF, elemento de gráfico de Editor u otro tipo de proyecto de extensibilidad que incluye un manifiesto VSIX.  
  
2. Abra el manifiesto de VSIX en el editor de código.  
  
3. Establezca el elemento InstalledByMsi de manifiesto VSIX para `true`. Para obtener más información sobre el manifiesto VSIX, vea [VSIX extensión de esquema 2.0 referencia](../extensibility/vsix-extension-schema-2-0-reference.md).  
  
     Esto impide que el instalador de VSIX intentando instalar el componente.  
  
4. Haga clic en el proyecto en **el Explorador de soluciones** y haga clic en **propiedades**.  
  
5. Seleccione el **VSIX** ficha.  
  
6. Active la casilla denominada **contenido de VSIX de copia en la siguiente ubicación** y escriba la ruta de acceso donde el proyecto de instalación recogerá los archivos.  
  
## <a name="extracting-files-from-an-existing-vsix-package"></a>Extraer archivos de un paquete VSIX existente  
 Siga estos pasos para agregar el contenido de un paquete VSIX existente a un proyecto de instalación cuando no tiene los archivos de origen.  
  
#### <a name="to-extract-files-from-an-existing-vsix-package"></a>Para extraer los archivos de un paquete VSIX existente  
  
1. Cambiar el nombre de la. Archivo VSIX que contiene la extensión de *filename*.vsix para *filename*zip.  
  
2. Copie el contenido del archivo zip en un directorio.  
  
3. Eliminar el archivo [Content_types] .xml desde el directorio.  
  
4. Editar el manifiesto VSIX, tal como se muestra en el procedimiento anterior.  
  
5. Agregue los archivos restantes al proyecto de instalación.  
  
## <a name="see-also"></a>Vea también  
 [Implementación del instalador de Visual Studio](https://msdn.microsoft.com/121be21b-b916-43e2-8f10-8b080516d2a0)   
 [Tutorial: Creación de una acción personalizada](https://msdn.microsoft.com/4bd4b63a-2b91-431e-839c-5752443f0eaf)
