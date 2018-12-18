---
title: 'Cómo: habilitar y deshabilitar Editar y continuar | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- /INCREMENTAL linker option
- Apply Code Changes command
- Edit and Continue, disabling
- code changes, applying in break mode
- INCREMENTAL linker option
- Edit and Continue, enabling
- break mode, applying code changes
- Edit and Continue, applying code changes
- Step command
- Go command
ms.assetid: fd961a1c-76fa-420d-ad8f-c1a6c003b0db
caps.latest.revision: 29
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5709b4bdae55c0ade6ca4559dcbaad8d66c0bbac
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51781262"
---
# <a name="how-to-enable-and-disable-edit-and-continue"></a>Cómo: Habilitar y deshabilitar Editar y continuar
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Puede deshabilitar o Habilitar Editar y continuar en el **opciones** cuadro de diálogo en tiempo de diseño. No puede cambiar este valor mientras esté depurando.  
  
 Editar y continuar solo funciona en las compilaciones de depuración. En C++ nativo, Editar y continuar requiere el uso de la opción /INCREMENTAL.  
  
## <a name="procedures"></a>Procedimientos  
  
#### <a name="to-enabledisable-edit-and-continue"></a>Para habilitar o deshabilitar Editar y continuar  
  
1. Abrir página de opciones de depuración (**herramientas / opciones / depuración**).  
  
2. Desplácese hacia abajo hasta **editar y continuar** categoría.  
  
3. Para habilitar esta opción, seleccione el **Habilitar Editar y continuar** casilla de verificación. Para deshabilitarla, desactive la casilla.  
  
   > [!NOTE]
   >  Si se habilita IntelliTrace y se recopilan eventos de IntelliTrace e información de llamadas, se deshabilita Editar y continuar. Para obtener más información, consulte [configurar IntelliTrace](http://msdn.microsoft.com/en-us/7657ecab-e07e-4b1b-872d-f05d966be37e).  
  
4. Haga clic en **Aceptar**.  
  
   Para obtener más información acerca de estas opciones, consulte [General, depuración, cuadro de diálogo Opciones](../debugger/general-debugging-options-dialog-box.md).  
  
## <a name="see-also"></a>Vea también  
 [Editar y continuar](../debugger/edit-and-continue.md)



