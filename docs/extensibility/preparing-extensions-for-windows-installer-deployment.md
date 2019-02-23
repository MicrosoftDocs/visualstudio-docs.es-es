---
title: Preparación de las extensiones para la implementación de Windows Installer | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- vsix msi
ms.assetid: 5ee2d1ba-478a-4cb7-898f-c3b4b2ee834e
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2f37ed2819e1c5999c7d225e52f652ebef3bd7da
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/22/2019
ms.locfileid: "56692117"
---
# <a name="prepare-extensions-for-windows-installer-deployment"></a>Preparar las extensiones para la implementación de Windows Installer
No se puede usar un paquete de Windows Installer (MSI) para implementar un paquete VSIX. Sin embargo, puede extraer el contenido de un paquete VSIX para la implementación de MSI. Este documento muestra cómo preparar un proyecto cuya salida predeterminada es un paquete VSIX para su inclusión en un proyecto de instalación.

## <a name="prepare-an-extension-project-for-windows-installer-deployment"></a>Preparar un proyecto de extensión para la implementación de Windows Installer
 Realice estos pasos en nuevos proyectos de extensión antes de agregar a un proyecto de instalación.

### <a name="to-prepare-an-extension-project-for-windows-installer-deployment"></a>Para preparar un proyecto de extensión para la implementación de Windows Installer

1.  Crear un VSPackage, el componente MEF, elemento de gráfico de Editor u otro tipo de proyecto de extensibilidad que incluye un manifiesto VSIX.

2.  Abra el manifiesto de VSIX en el editor de código.

3.  Establecer el `InstalledByMsi` elemento del manifiesto VSIX para `true`. Para obtener más información sobre el manifiesto VSIX, vea [referencia de esquema 2.0 de extensión VSIX](../extensibility/vsix-extension-schema-2-0-reference.md).

     Esto impide que el instalador de VSIX intentando instalar el componente.

4.  Haga clic en el proyecto en **el Explorador de soluciones** y haga clic en **propiedades**.

5.  Seleccione el **VSIX** ficha.

6.  Active la casilla denominada **contenido de VSIX de copia en la siguiente ubicación** y escriba la ruta de acceso donde el proyecto de instalación recogerá los archivos.

## <a name="extract-files-from-an-existing-vsix-package"></a>Extraiga los archivos de un paquete VSIX existente
 Siga estos pasos para agregar el contenido de un paquete VSIX existente a un proyecto de instalación cuando no tiene los archivos de origen.

### <a name="to-extract-files-from-an-existing-vsix-package"></a>Para extraer los archivos de un paquete VSIX existente

1.  Cambiar el nombre de la *. VSIX* archivo que contiene la extensión de *filename.vsix* a *filename.zip*.

2.  Copie el contenido de la *.zip* archivo en un directorio.

3.  Eliminar el *[Content_types] .xml* archivo desde el directorio.

4.  Editar el manifiesto VSIX, tal como se muestra en el procedimiento anterior.

5.  Agregue los archivos restantes al proyecto de instalación.

## <a name="see-also"></a>Vea también
- [Implementación del instalador de Visual Studio](https://msdn.microsoft.com/library/121be21b-b916-43e2-8f10-8b080516d2a0)
- [Tutorial: Crear una acción personalizada](/previous-versions/visualstudio/visual-studio-2010/d9k65z2d(v=vs.100))