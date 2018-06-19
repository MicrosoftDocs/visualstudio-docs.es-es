---
title: 'Cómo: agregar una dependencia a un paquete VSIX | Documentos de Microsoft'
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
ms.openlocfilehash: 0704a72ba70e2a00baab99d327702ec6c08f1775
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
ms.locfileid: "31133227"
---
# <a name="how-to-add-a-dependency-to-a-vsix-package"></a>Cómo: agregar una dependencia a un paquete VSIX

Puede configurar la implementación de un paquete VSIX que instala cualquier dependencia que ya no está presente en el equipo de destino. Para ello, incluya las dependencias VSIX en el archivo source.extension.vsixmanifest.

## <a name="to-add-a-dependency"></a>Para agregar una dependencia

1. Abra el archivo source.extension.vsixmanifest en el **diseño** vista. Vaya a la **dependencias** ficha y haga clic en **nuevo**.

2. Para agregar una extensión instalada: en el **agregar nuevas dependencias** cuadro de diálogo, seleccione **extensión instalada** y, después, en la **nombre**, seleccione una extensión en la lista.

3. Para agregar otro VSIX que no está instalado:: en el **agregar nuevas dependencias** cuadro de diálogo, seleccione **archivo en el sistema de archivos** y, a continuación, use la **examinar** para seleccionar la extensión VSIX.

## <a name="require-a-specific-visual-studio-release"></a>Requiere una versión específica de Visual Studio

Si la extensión requiere una versión específica de 2017 de Visual Studio, por ejemplo, depende de una característica que se han publicado en 15.3, puede especificar el número de compilación en el VSIX **InstallationTarget**. Por ejemplo, versión 15.3 tiene un número de compilación de '15.0.26730.3'. Puede ver la asignación de versiones para generar números [aquí](../install/visual-studio-build-numbers-and-release-dates.md). Tenga en cuenta que el número de versión '15.3' no funcionará correctamente.

Si la extensión requiere 15.3 o versiones posteriores, declararía el **InstallationTarget versión** como [15.0.26730.3, 16.0):

```xml
<Installation>
  <InstallationTarget Id="Microsoft.VisualStudio.Community" Version="[15.0.26730.3, 16.0)" />
</Installation>
```

El VSIXInstaller detectará las versiones anteriores de Visual Studio e informar al usuario que se requiere una actualización posterior.


## <a name="see-also"></a>Vea también

 [Referencia de esquema 1.0 de extensión VSIX](http://msdn.microsoft.com/en-us/76e410ec-b1fb-4652-ac98-4a4c52e09a2b) [Anatomía de un paquete VSIX](../extensibility/anatomy-of-a-vsix-package.md) [preparar las extensiones para la implementación de Windows Installer](../extensibility/preparing-extensions-for-windows-installer-deployment.md)