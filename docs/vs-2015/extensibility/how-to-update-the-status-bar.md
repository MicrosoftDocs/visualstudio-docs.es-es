---
title: 'Cómo: actualizar la barra de estado | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - update status bar
ms.assetid: 7500c8a7-4913-4818-a88b-bfd1b9887cb6
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 1d48b07dd5e4fc1fe745e3669041884c1b8eacd9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "65703147"
---
# <a name="how-to-update-the-status-bar"></a>Cómo: Actualizar la barra de estado
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La **barra de estado** es una barra de controles que se encuentra en la parte inferior de muchas ventanas de aplicación que contiene una o más líneas de texto de estado o indicadores.  
  
### <a name="to-update-the-status-bar"></a>Para actualizar la barra de estado  
  
1. Implemente <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser> en cada objeto de vista individual (docview) que proporcione el editor, como una vista de formulario y una vista de código.  
  
2. Cuando el IDE llama a <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A> , actualice la información de la **barra de estado** mediante una llamada a los métodos de <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser> .  
  
    > [!NOTE]
    > El IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A> solo llama cuando la ventana de documento se activa inicialmente. Durante el resto del tiempo que la ventana de documento está activa, debe actualizar la información de la **barra de estado** a medida que cambia el estado del editor.  
  
## <a name="robust-programming"></a>Programación sólida  
 Una **barra de estado** contiene cuatro campos independientes:  
  
- Texto de estado  
  
- Barra de progreso  
  
- Icono animado  
  
- Información del editor  
  
  Para obtener más información, vea [barras de estado](https://msdn.microsoft.com/library/fcbc5029-1aab-4e14-adf7-419038a4935e).  
  
  El IDE llama automáticamente al <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A> método de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser> implementación cuando se activa la ventana de documento.  
  
  El implementador de VSPackage es responsable de actualizar el texto de estado en la barra de estado. El IDE restablece esta cadena en "READY" si el campo de texto de estado se establece en texto vacío ("") en tiempo de inactividad.  
  
## <a name="see-also"></a>Consulte también  
 [Barras de estado](https://msdn.microsoft.com/library/fcbc5029-1aab-4e14-adf7-419038a4935e)
