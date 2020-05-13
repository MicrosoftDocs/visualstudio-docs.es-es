---
title: 'Cómo: Agregar una dependencia a un paquete VSIX Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- package reference
- package assembly
- package dll
- vsix reference
ms.assetid: 8f20177b-dab9-43a3-b959-81a591b451d6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f8b350f063c28762edf90edfe71330534451c75d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711077"
---
# <a name="how-to-add-a-dependency-to-a-vsix-package"></a>Cómo: Agregar una dependencia a un paquete VSIX

Puede configurar una implementación de paquete VSIX que instale las dependencias que aún no estén presentes en el equipo de destino. Para ello, incluya las dependencias VSIX en el archivo *source.extension.vsixmanifest.*

## <a name="to-add-a-dependency"></a>Para agregar una dependencia

1. Abra el archivo *source.extension.vsixmanifest* en la vista **Diseño.** Vaya a la pestaña **Dependencias** y haga clic en **Nuevo**.

2. Para agregar una extensión instalada: en el cuadro de diálogo **Agregar nueva dependencia,** seleccione **Extensión instalada** y, a continuación, en **Nombre**, seleccione una extensión en la lista.

3. Para agregar otro VSIX que no esté instalado: en el cuadro de diálogo **Agregar nueva dependencia,** seleccione **Archivo en** el sistema de archivos y, a continuación, utilice el botón **Examinar** para seleccionar VSIX.

## <a name="require-a-specific-visual-studio-release"></a>Requerir una versión específica de Visual Studio

Si la extensión requiere una versión específica de Visual Studio 2017, por ejemplo, depende de una característica publicada en 15.3, puede especificar el número de compilación en VSIX **InstallationTarget**. Por ejemplo, la versión 15.3 tiene un número de compilación de '15.0.26730.3'. Puede ver la asignación de versiones para generar números [aquí.](../install/visual-studio-build-numbers-and-release-dates.md) Tenga en cuenta que el uso del número de versión '15.3' no funcionará correctamente.

Si la extensión requiere 15.3 o superior, declararía la **versión InstallationTarget** como [15.0.26730.3, 16.0):

```xml
<Installation>
  <InstallationTarget Id="Microsoft.VisualStudio.Community" Version="[15.0.26730.3, 16.0)" />
</Installation>
```

VSIXInstaller detectará versiones anteriores de Visual Studio e informará al usuario de que se requiere una actualización posterior.

## <a name="see-also"></a>Vea también

- [Referencia del esquema de extensión VSIX 1.0](https://msdn.microsoft.com/library/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)
- [Anatomía de un paquete VSIX](../extensibility/anatomy-of-a-vsix-package.md)
- [Preparar extensiones para la implementación de Windows Installer](../extensibility/preparing-extensions-for-windows-installer-deployment.md)
