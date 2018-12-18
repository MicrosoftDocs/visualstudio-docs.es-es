---
title: 'Cómo: actualizar la barra de estado | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - update status bar
ms.assetid: 7500c8a7-4913-4818-a88b-bfd1b9887cb6
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: eb70e8799b74f470a2216a63aae4637fe1872681
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51768351"
---
# <a name="how-to-update-the-status-bar"></a>Cómo: actualizar la barra de estado
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

El **barra de estado** se encuentra una barra de controles en la parte inferior de muchas ventanas de aplicación que contiene una o varias líneas de texto de estado o los indicadores.  
  
### <a name="to-update-the-status-bar"></a>Para actualizar la barra de estado  
  
1.  Implemente <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser> en cada objeto de vista individuales (DocView) que proporciona el editor, como una vista de formulario y una vista de código.  
  
2.  Cuando se llama el IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A>, actualizar la información en el **barra de estado** mediante una llamada a los métodos de <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser>.  
  
    > [!NOTE]
    >  Las llamadas IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A> solo cuando se activa inicialmente la ventana de documento. El resto del tiempo que la ventana de documento está activa, debe actualizar el **barra de estado** información como el estado de los cambios del editor.  
  
## <a name="robust-programming"></a>Programación sólida  
 Un **barra de estado** contiene cuatro campos independientes:  
  
- Texto de estado  
  
- Barra de progreso  
  
- Icono animado  
  
- Información del Editor  
  
  Para obtener más información, consulte [barras de estado](http://msdn.microsoft.com/library/fcbc5029-1aab-4e14-adf7-419038a4935e).  
  
  El IDE llama automáticamente a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A> método de su <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser> implementación cuando se activa la ventana de documento.  
  
  El implementador de VSPackage es responsable de actualizar el texto de estado en la barra de estado. El IDE restablece esta cadena a "Listo" si el campo de texto de estado se establece en texto vacío ("") en tiempo de inactividad.  
  
## <a name="see-also"></a>Vea también  
 [Barras de estado](http://msdn.microsoft.com/library/fcbc5029-1aab-4e14-adf7-419038a4935e)

