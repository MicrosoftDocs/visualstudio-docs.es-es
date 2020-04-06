---
title: Preparación de extensiones para la implementación de Windows Installer ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- vsix msi
ms.assetid: 5ee2d1ba-478a-4cb7-898f-c3b4b2ee834e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8636dfbbad06192e5edbb61a9a784f64b8f3f14f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702027"
---
# <a name="prepare-extensions-for-windows-installer-deployment"></a>Preparar extensiones para la implementación de Windows Installer
No puede usar un paquete de Windows Installer (MSI) para implementar un paquete VSIX. Sin embargo, puede extraer el contenido de un paquete VSIX para la implementación msi. Este documento muestra cómo preparar un proyecto cuya salida predeterminada es un paquete VSIX para su inclusión en un proyecto de instalación.

## <a name="prepare-an-extension-project-for-windows-installer-deployment"></a>Preparar un proyecto de extensión para la implementación de Windows Installer
 Realice estos pasos en nuevos proyectos de extensión antes de agregara a un proyecto de instalación.

### <a name="to-prepare-an-extension-project-for-windows-installer-deployment"></a>Para preparar un proyecto de extensión para la implementación de Windows Installer

1. Cree un VSPackage, componente MEF, Editor Adornment u otro tipo de proyecto de extensibilidad que incluya un manifiesto VSIX.

2. Abra el manifiesto VSIX en el editor de código.

3. Establezca `InstalledByMsi` el elemento del manifiesto `true`VSIX en . Para obtener más información sobre el manifiesto VSIX, vea Referencia 2.0 del esquema de [extensión VSIX.](../extensibility/vsix-extension-schema-2-0-reference.md)

     Esto impide que el instalador de VSIX intente instalar el componente.

4. Haga clic con el botón derecho en el proyecto en el **Explorador** de soluciones y haga clic en **Propiedades**.

5. Seleccione la pestaña **VSIX.**

6. Active la casilla **Copiar contenido VSIX en la siguiente ubicación** y escriba la ruta de acceso a donde el proyecto de instalación recogerá los archivos.

## <a name="extract-files-from-an-existing-vsix-package"></a>Extraer archivos de un paquete VSIX existente
 Realice estos pasos para agregar el contenido de un paquete VSIX existente a un proyecto de instalación cuando no tenga los archivos de origen.

### <a name="to-extract-files-from-an-existing-vsix-package"></a>Para extraer archivos de un paquete VSIX existente

1. Cambie el nombre del *archivo . VSIX* que contiene la extensión de *filename.vsix* a *filename.zip*.

2. Copie el contenido del archivo *.zip* en un directorio.

3. Elimine el archivo *[Content_types].xml* del directorio.

4. Edite el manifiesto VSIX, tal y como se muestra en del procedimiento anterior.

5. Agregue los archivos restantes al proyecto de instalación.

## <a name="see-also"></a>Vea también
- [Implementación del instalador de Visual Studio](https://msdn.microsoft.com/library/121be21b-b916-43e2-8f10-8b080516d2a0)
- [Tutorial: Crear una acción personalizada](/previous-versions/visualstudio/visual-studio-2010/d9k65z2d(v=vs.100))
