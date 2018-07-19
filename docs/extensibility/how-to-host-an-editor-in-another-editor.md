---
title: 'Cómo: hospedar un Editor en otro Editor | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - host a nested editor
ms.assetid: 2b0eb705-fe94-4ca8-93e0-9dbd8ce61a44
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 53b4f02135b18c4641d4e802df3d1124a5d06b47
ms.sourcegitcommit: 0bf2aff6abe485e3fe940f5344a62a885ad7f44e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/27/2018
ms.locfileid: "37058391"
---
# <a name="how-to-host-an-editor-in-another-editor"></a>Cómo: hospedar un editor en otro editor

En Visual Studio, puede hospedar un editor dentro de otra mediante la especificación de la ventana de hospedaje como una ventana primaria. Para ello, establezca los parámetros <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID2.VSFPROPID_ParentHwnd> y <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID2.VSFPROPID_ParentFrame> en el marco de ventana secundaria.

## <a name="to-set-up-the-window-frame-to-host-an-editor"></a>Para configurar el marco de ventana para hospedar un editor

1.  Designar un editor como un editor hospedado mediante la creación de un panel de ventana secundaria.

     Este panel es donde pasará texto del editor.

2.  Crear el editor de hospedaje mediante la <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> o <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenSpecificEditor%2A> método.

3.  Establecer el <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID2.VSFPROPID_ParentHwnd> y <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID2.VSFPROPID_ParentFrame> propiedades en la implementación del marco de ventana del editor hospedado pasando estas propiedades como parámetros para el <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.SetProperty%2A> método, respectivamente.

     Si necesita recuperar estos parámetros, pase estas propiedades para el <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> método.

4.  Llame a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A> método para el editor independiente.

     Aparece el editor en el panel del editor de contenedor hospedado.

## <a name="robust-programming"></a>Programación sólida

El **Application Designer** en Visual Studio Team Edition para Architects es un ejemplo de un marco de ventana del editor hospeda otro editor. El **Application Designer** hospeda otros diseñadores en el panel derecho. Un panel del diseñador (o **propiedades** página) para cada uno de los diseñadores contenidos se agrega en el marco de ventana que lo contiene.