---
title: Filtrar Mostrar información de seguimiento WPF | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- WPF, debugging
- debugging, WPF
ms.assetid: be3c6859-06e1-459e-9fd0-46375b5f55ef
caps.latest.revision: 16
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 7a25d2bf4c814bf946aa64cfb126e119f50913d5
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "58996178"
---
# <a name="how-to-display-wpf-trace-information"></a>Filtrar Presentación de información de seguimiento de WPF
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] puede recibir información de seguimiento de la depuración de las aplicaciones WPF y mostrar esa información en la ventana **Salida**. Para mostrar la información de seguimiento de depuración, debe estar habilitada la traza de WPF.  
  
 Puede habilitar la traza de WPF en su archivo App.Config o, mediante programación, utilizando la clase <xref:System.Diagnostics.PresentationTraceSources>. Una manera más fácil de habilitar la traza de WPF es usar la ventana **Opciones**. No se admite la traza WPF en las aplicaciones web.  
  
### <a name="to-enable-or-customize-wpf-trace-information"></a>Para habilitar o personalizar la información de seguimiento de WPF  
  
1.  En el menú **Herramientas**, seleccione **Opciones**.  
  
2.  En el cuadro de diálogo **Opciones**, en el cuadro de la izquierda, abra el nodo **Depuración**.  
  
3.  En **Depuración**, haga clic en **Ventana de salida**.  
  
4.  En **Configuración general de salida**, seleccione **Toda la salida de depuración**.  
  
5.  En el cuadro de la derecha, busque **Configuración de seguimiento de WPF**.  
  
6.  Abra el nodo **Configuración de seguimiento de WPF**.  
  
7.  En **Configuración de seguimiento de WPF**, haga clic en la categoría de valores que desea habilitar (por ejemplo, **Enlace de datos**).  
  
     Aparecerá un control de lista desplegable en la columna Configuración, al lado de **Enlace de datos** o de la categoría en la que haya hecho clic.  
  
8.  Haga clic en la lista desplegable y seleccione el tipo de información de seguimiento que desea ver: **Todos los**, **críticos**, **Error**, **advertencia**, **información**, **detallado**, o **ActivityTracing**.  
  
     **Critical** solo habilita la traza de los eventos críticos.  
  
     **Error** habilita la traza de los eventos críticos y de error.  
  
     **Warning** habilita la traza de los eventos críticos, de error y de advertencia.  
  
     **Information** habilita la traza de los eventos críticos, de error, de advertencia y de información.  
  
     **Verbose** habilita la traza de los eventos críticos, de error, de advertencia, de información y detallados.  
  
     **ActivityTracing** habilita la traza de los eventos de detención, inicio, suspensión, transferencia y reanudación.  
  
     Para obtener más información sobre el significado de estos niveles de información de seguimiento, vea <xref:System.Diagnostics.SourceLevels>.  
  
9. Haga clic en **Aceptar**.  
  
### <a name="to-disable-wpf-trace-information"></a>Para deshabilitar la información de seguimiento de WPF  
  
1.  En el menú **Herramientas**, seleccione **Opciones**.  
  
2.  En el cuadro de diálogo **Opciones**, en el cuadro de la izquierda, abra el nodo **Depuración**.  
  
3.  En **Depuración**, haga clic en **Ventana de salida**.  
  
4.  En el cuadro de la derecha, busque **Configuración de seguimiento de WPF**.  
  
5.  Abra el nodo **Configuración de seguimiento de WPF**.  
  
6.  En **Configuración de seguimiento de WPF**, haga clic en la categoría de valores que desea habilitar (por ejemplo, **Enlace de datos**).  
  
     Aparecerá un control de lista desplegable en la columna Configuración, al lado de **Enlace de datos** o de la categoría en la que haya hecho clic.  
  
7.  Haga clic en la lista desplegable y seleccione **Desactivado**.  
  
8.  Haga clic en **Aceptar**.  
  
## <a name="see-also"></a>Vea también  
 [Depurar WPF](../debugger/debugging-wpf.md)
