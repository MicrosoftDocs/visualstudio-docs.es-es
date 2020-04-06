---
title: Automatización de la configuración y objetos SelectedItem Microsoft Docs
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709971"
---
# <a name="automation-for-configuration-and-selecteditem-objects"></a>Automatización para objetos Configuration y SelectedItem

Puede automatizar los procesos de compilación y elemento seleccionado en Visual Studio.

## <a name="automation-for-builds"></a>Automatización para compilaciones

La compilación o configuración tiene un modelo <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider>de automatización que se proporciona al implementar . Para obtener más información, vea [Descripción de las configuraciones de compilación](../../ide/understanding-build-configurations.md).

Si crea un VSPackage y desea controlar las opciones de configuración, debe usar el modelo de automatización.

## <a name="automation-for-selecteditem"></a>Automatización para SelectedItem

No es necesario proporcionar una `SelectedItem` implementación para el objeto porque Visual Studio contiene una implementación estándar. Sin embargo, `SelectedItem` puede implementar el objeto si lo prefiere. Debe implementar un objeto `SelectedItem` que contenga la interfaz y <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> devolver `VSITEMID` una respuesta a una llamada al método con establecido en [__VSHPROPID. VSHPROPID_ExtSelectedItem](<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_ExtSelectedItem>).

## <a name="see-also"></a>Vea también

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A>
- [Contribuir al modelo de automatización](../../extensibility/internals/contributing-to-the-automation-model.md)
- [Descripción de las configuraciones de compilación](../../ide/understanding-build-configurations.md)
