---
title: Automatización para objetos Configuration y SelectedItem | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK], SelectedItem object
- automation [Visual Studio SDK], builds
ms.assetid: 120377f1-51aa-4445-b2f7-06ab7fc2b47f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0341cdf56b32b8b1ac77104b3f3e813ae0610767
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "80709971"
---
# <a name="automation-for-configuration-and-selecteditem-objects"></a>Automatización para objetos Configuration y SelectedItem

Puede automatizar los procesos de compilación y elementos seleccionados en Visual Studio.

## <a name="automation-for-builds"></a>Automatización para compilaciones

La compilación o configuración tiene un modelo de automatización que se proporciona al implementar <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider> . Para obtener más información, vea [Descripción de las configuraciones de compilación](../../ide/understanding-build-configurations.md).

Si crea un VSPackage y desea controlar las opciones de configuración, debe utilizar el modelo de automatización.

## <a name="automation-for-selecteditem"></a>Automatización para SelectedItem

No es necesario proporcionar una implementación para el `SelectedItem` objeto porque Visual Studio contiene una implementación estándar. Sin embargo, puede implementar el `SelectedItem` objeto si lo prefiere. Debe implementar un objeto que contenga la `SelectedItem` interfaz y devolver una respuesta a una llamada al <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> método con `VSITEMID` establecido en [__VSHPROPID. VSHPROPID_ExtSelectedItem](<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_ExtSelectedItem>).

## <a name="see-also"></a>Vea también

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A>
- [Contribuir al modelo de automatización](../../extensibility/internals/contributing-to-the-automation-model.md)
- [Descripción de las configuraciones de compilación](../../ide/understanding-build-configurations.md)
