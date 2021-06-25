---
title: Automatización de la configuración y los objetos SelectedItem | Microsoft Docs
description: Obtenga información sobre cómo automatizar los Visual Studio compilación y los procesos de elementos seleccionados mediante los objetos Configuration y SelectedItem en interoperabilidad de shell.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- automation [Visual Studio SDK], SelectedItem object
- automation [Visual Studio SDK], builds
ms.assetid: 120377f1-51aa-4445-b2f7-06ab7fc2b47f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 1a95fc06c5d84a936cdb1ada3369f584381dfe7f
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112901635"
---
# <a name="automation-for-configuration-and-selecteditem-objects"></a>Automatización para objetos Configuration y SelectedItem

Puede automatizar los procesos de compilación y elementos seleccionados en Visual Studio.

## <a name="automation-for-builds"></a>Automatización para compilaciones

La compilación o configuración tiene un modelo de automatización que se proporciona al implementar <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider> . Para obtener más información, vea [Descripción de las configuraciones de compilación](../../ide/understanding-build-configurations.md).

Si crea un VSPackage y desea controlar las opciones de configuración, debe usar el modelo de automatización.

## <a name="automation-for-selecteditem"></a>Automation para SelectedItem

No es necesario proporcionar una implementación para el objeto porque Visual Studio `SelectedItem` una implementación estándar. Sin embargo, puede implementar el `SelectedItem` objeto si lo prefiere. Debe implementar un objeto que contenga la interfaz y devolver una respuesta a una llamada al método `SelectedItem` <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> con establecido en `VSITEMID` [__VSHPROPID. VSHPROPID_ExtSelectedItem](<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_ExtSelectedItem>).

## <a name="see-also"></a>Consulta también

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A>
- [Contribución al modelo de automatización](../../extensibility/internals/contributing-to-the-automation-model.md)
- [Descripción de las configuraciones de compilación](../../ide/understanding-build-configurations.md)
