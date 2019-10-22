---
title: Automatización de la configuración y objetos SelectedItem | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK], SelectedItem object
- automation [Visual Studio SDK], builds
ms.assetid: 120377f1-51aa-4445-b2f7-06ab7fc2b47f
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e6c9dc8012433f9ec73f15b9249f6b7ac08bdad7
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "66347976"
---
# <a name="automation-for-configuration-and-selecteditem-objects"></a>Automatización de los objetos de configuración y SelectedItem

Puede automatizar la compilación y el elemento seleccionado de procesos en Visual Studio.

## <a name="automation-for-builds"></a>Automatización de compilaciones

Compilación o la configuración tiene un modelo de automatización que se proporciona al implementar <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider>. Para obtener más información, vea [Descripción de las configuraciones de compilación](../../ide/understanding-build-configurations.md).

Si crea un VSPackage y desea controlar las opciones de configuración, debe usar el modelo de automatización.

## <a name="automation-for-selecteditem"></a>Automatización de SelectedItem

No es necesario proporcionar una implementación para el `SelectedItem` porque Visual Studio contiene una implementación estándar de objeto. Sin embargo, puede implementar la `SelectedItem` objeto si lo prefiere. Debe implementar un objeto que contiene el `SelectedItem` interfaz y devolver una respuesta a una llamada a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> método con `VSITEMID` establecido en [__VSHPROPID. VSHPROPID_ExtSelectedItem](<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_ExtSelectedItem>).

## <a name="see-also"></a>Vea también

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A>
- [Contribuir al modelo de automatización](../../extensibility/internals/contributing-to-the-automation-model.md)
- [Descripción de las configuraciones de compilación](../../ide/understanding-build-configurations.md)