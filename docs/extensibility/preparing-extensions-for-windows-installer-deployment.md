---
title: Preparando extensiones para la implementación de Windows Installer | Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- vsix msi
ms.assetid: 5ee2d1ba-478a-4cb7-898f-c3b4b2ee834e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0084cfc6c08db1c1d15013362a186fec175b4ee4
ms.sourcegitcommit: 4b29efeb3a5f05888422417c4ee236e07197fb94
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/11/2020
ms.locfileid: "90012222"
---
# <a name="prepare-extensions-for-windows-installer-deployment"></a>Preparar las extensiones para la implementación de Windows Installer
No se puede usar un paquete de Windows Installer (MSI) para implementar un paquete VSIX. Sin embargo, puede extraer el contenido de un paquete VSIX para la implementación de MSI. En este documento se muestra cómo preparar un proyecto cuya salida predeterminada es un paquete VSIX para su inclusión en un proyecto de instalación.

## <a name="prepare-an-extension-project-for-windows-installer-deployment"></a>Preparar un proyecto de extensión para la implementación de Windows Installer
 Siga estos pasos en los nuevos proyectos de extensión antes de agregarlos a un proyecto de instalación.

### <a name="to-prepare-an-extension-project-for-windows-installer-deployment"></a>Para preparar un proyecto de extensión para la implementación de Windows Installer

1. Cree un VSPackage, un componente MEF, un elemento gráfico del editor u otro tipo de proyecto de extensibilidad que incluya un manifiesto VSIX.

2. Abra el manifiesto de VSIX en el editor de código.

3. Establezca el `InstalledByMsi` elemento del manifiesto VSIX en `true` . Para obtener más información sobre el manifiesto VSIX, vea [referencia de esquema de extensión vsix 2,0](../extensibility/vsix-extension-schema-2-0-reference.md).

     Esto evita que el instalador de VSIX intente instalar el componente.

4. Haga clic con el botón derecho en el proyecto en **Explorador de soluciones** y haga clic en **propiedades**.

5. Seleccione la pestaña **VSIX** .

6. Active la casilla con la etiqueta **copiar contenido VSIX en la siguiente ubicación** y escriba la ruta de acceso donde el proyecto de instalación recogerá los archivos.

## <a name="extract-files-from-an-existing-vsix-package"></a>Extraer archivos de un paquete VSIX existente
 Siga estos pasos para agregar el contenido de un paquete VSIX existente a un proyecto de instalación si no tiene los archivos de código fuente.

### <a name="to-extract-files-from-an-existing-vsix-package"></a>Para extraer archivos de un paquete VSIX existente

1. Cambie el nombre del *. Archivo VSIX* que contiene la extensión de *filename. vsix* a *filename.zip*.

2. Copie el contenido del archivo *. zip* en un directorio.

3. Elimine el archivo *[Content_types]. XML* del directorio.

4. Edite el manifiesto de VSIX, tal como se muestra en el procedimiento anterior.

5. Agregue los archivos restantes al proyecto de instalación.

## <a name="see-also"></a>Vea también
- [Implementación del instalador de Visual Studio](/previous-versions/2kt85ked(v=vs.120))
- [Tutorial: crear una acción personalizada](/previous-versions/visualstudio/visual-studio-2010/d9k65z2d(v=vs.100))