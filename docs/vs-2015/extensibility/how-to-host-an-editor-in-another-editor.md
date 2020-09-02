---
title: 'Cómo: hospedar un editor en otro editor | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - host a nested editor
ms.assetid: 2b0eb705-fe94-4ca8-93e0-9dbd8ce61a44
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 4d4b4ff425feb22b5057a8d1a76b7f73b8932d9f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204169"
---
# <a name="how-to-host-an-editor-in-another-editor"></a>Cómo: Hospedar un editor en otro editor
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

En Visual Studio, puede hospedar un editor dentro de otro especificando la ventana de hospedaje como ventana primaria. Para ello, establezca los parámetros <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID2> y <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID2> en el marco de la ventana secundaria.  
  
### <a name="to-set-up-the-window-frame-to-host-an-editor"></a>Para configurar el marco de ventana para hospedar un editor  
  
1. Designe un editor como editor hospedado mediante la creación de un panel de ventana secundario.  
  
     Este panel es el lugar en el que irá el texto del editor.  
  
2. Cree el editor de hospedaje mediante <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> el <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenSpecificEditor%2A> método o.  
  
3. Establezca las <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID2> <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID2> propiedades y en la implementación de marco de ventana del editor hospedado pasando estas propiedades como parámetros al <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.SetProperty%2A> método, respectivamente.  
  
     Si necesita recuperar estos parámetros, pase estas propiedades al <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> método.  
  
4. Llame al <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A> método para el editor contenido.  
  
     El editor aparece en el panel hospedado del editor contenedor.  
  
## <a name="robust-programming"></a>Programación sólida  
 La **Diseñador de aplicaciones** de Visual Studio Team Edition para Architects es un ejemplo de un marco de ventana del editor que hospeda otro editor. El **Diseñador de aplicaciones** hospeda a otros diseñadores en el panel derecho. Un panel del diseñador (o página de **propiedades** ) para cada uno de los diseñadores incluidos se agrega al marco de la ventana que lo contiene.
