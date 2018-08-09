---
title: 'Cómo: agregar una dependencia a un paquete VSIX | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- package reference
- package assembly
- package dll
- vsix reference
ms.assetid: 8f20177b-dab9-43a3-b959-81a591b451d6
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 54b4bf86df74a60dbeabef5c6f375354c5a945aa
ms.sourcegitcommit: 06db1892fff22572f0b0a11994dc547c2b7e2a48
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/08/2018
ms.locfileid: "39636693"
---
# <a name="how-to-add-a-dependency-to-a-vsix-package"></a>Cómo: agregar una dependencia a un paquete VSIX

Puede configurar una implementación de paquete VSIX que instala las dependencias que no están presentes en el equipo de destino. Para ello, incluyen las dependencias VSIX para la *source.extension.vsixmanifest* archivo.

## <a name="to-add-a-dependency"></a>Para agregar una dependencia

1. Abra el *source.extension.vsixmanifest* de archivos en el **diseño** vista. Vaya a la **dependencias** ficha y haga clic en **New**.

2. Para agregar una extensión instalada: en el **agregar nuevas dependencias** cuadro de diálogo, seleccione **extensión instalada** y, después, en el **nombre**, seleccione una extensión en la lista.

3. Para agregar otra extensión VSIX que no está instalado: en el **agregar nuevas dependencias** cuadro de diálogo, seleccione **archivo en el sistema de archivos** y, a continuación, utilice el **examinar** botón para seleccionar el archivo VSIX.

## <a name="require-a-specific-visual-studio-release"></a>Requerir una versión específica de Visual Studio

Si la extensión requiere una versión específica de Visual Studio 2017, por ejemplo, depende de una característica publicada en la versión 15.3, puede especificar el número de compilación en el proyecto de VSIX **InstallationTarget**. Por ejemplo, versión 15.3 tiene un número de compilación de '15.0.26730.3'. Puede ver la asignación de versiones para números de compilación [aquí](../install/visual-studio-build-numbers-and-release-dates.md). Tenga en cuenta que el número de versión 'versión ' 15.3 no funcionará correctamente.

Si la extensión requiere 15.3 o versiones posteriores, declararía la **InstallationTarget versión** como [15.0.26730.3, 16.0):

```xml
<Installation>
  <InstallationTarget Id="Microsoft.VisualStudio.Community" Version="[15.0.26730.3, 16.0)" />
</Installation>
```

El VSIXInstaller detectará las versiones anteriores de Visual Studio e informar al usuario que se requiere una actualización posterior.


## <a name="see-also"></a>Vea también

 [Referencia de esquema 1.0 de extensión VSIX](http://msdn.microsoft.com/en-us/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)   
 [Anatomía de un paquete VSIX](../extensibility/anatomy-of-a-vsix-package.md)   
 [Preparar las extensiones para la implementación de Windows Installer](../extensibility/preparing-extensions-for-windows-installer-deployment.md)
