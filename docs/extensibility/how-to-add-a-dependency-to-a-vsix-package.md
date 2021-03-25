---
title: 'Cómo: agregar una dependencia a un paquete VSIX | Microsoft Docs'
description: Obtenga información acerca de cómo configurar una implementación de paquetes VSIX que instala las dependencias que no están ya presentes en el equipo de destino.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- package reference
- package assembly
- package dll
- vsix reference
ms.assetid: 8f20177b-dab9-43a3-b959-81a591b451d6
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 48c6ac0abd5ffb6c36dc894829e29c9304563a5e
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105057408"
---
# <a name="how-to-add-a-dependency-to-a-vsix-package"></a>Cómo: agregar una dependencia a un paquete VSIX

Puede configurar una implementación de paquetes VSIX que instale las dependencias que no estén ya presentes en el equipo de destino. Para ello, incluya las dependencias de VSIX en el archivo *source. Extension. vsixmanifest* .

## <a name="to-add-a-dependency"></a>Para agregar una dependencia

1. Abra el archivo *source. Extension. vsixmanifest* en la vista de **diseño** . Vaya a la pestaña **dependencias** y haga clic en **nuevo**.

2. Para agregar una extensión instalada: en el cuadro de diálogo **Agregar nueva dependencia** , seleccione **extensión instalada** y, a continuación, para el **nombre**, seleccione una extensión de la lista.

3. Para agregar otra VSIX que no está instalada: en el cuadro de diálogo **Agregar nueva dependencia** , seleccione **archivo en el sistema de archivos** y, a continuación, use el botón **examinar** para seleccionar el VSIX.

## <a name="require-a-specific-visual-studio-release"></a>Requerir una versión específica de Visual Studio

Si la extensión requiere una versión específica de Visual Studio 2017, por ejemplo, depende de una característica publicada en 15,3, puede especificar el número de compilación en el **admitir** de VSIX. Por ejemplo, la versión 15,3 tiene un número de compilación de "15.0.26730.3". [Aquí](../install/visual-studio-build-numbers-and-release-dates.md)puede ver la asignación de versiones a los números de compilación. Tenga en cuenta que el uso del número de versión ' 15,3 ' no funcionará correctamente.

Si la extensión requiere 15,3 o superior, declararía la **versión de admitir** como [15.0.26730.3, 16,0):

```xml
<Installation>
  <InstallationTarget Id="Microsoft.VisualStudio.Community" Version="[15.0.26730.3, 16.0)" />
</Installation>
```

El VSIXInstaller detectará versiones anteriores de Visual Studio e informará al usuario de que se requiere una actualización posterior.

## <a name="see-also"></a>Consulte también

- [Referencia del esquema de extensión VSIX 1,0](/previous-versions/dd393700(v=vs.110))
- [Anatomía de un paquete VSIX](../extensibility/anatomy-of-a-vsix-package.md)
- [Preparar las extensiones para la implementación de Windows Installer](../extensibility/preparing-extensions-for-windows-installer-deployment.md)