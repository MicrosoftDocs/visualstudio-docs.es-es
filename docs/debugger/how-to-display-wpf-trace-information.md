---
title: para presentar información de seguimiento de WPF | Microsoft Docs
description: Visual Studio puede recibir información de seguimiento de la depuración de las aplicaciones de WPF y mostrarla en la ventana Salida. Obtenga información sobre cómo administrar y personalizar el seguimiento de WPF.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- WPF, debugging
- debugging, WPF
ms.assetid: be3c6859-06e1-459e-9fd0-46375b5f55ef
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0e4800c2ca44c2c52b2059685d9c5bc4fe38ed08
ms.sourcegitcommit: 620d30c60da8f9805fce524fe4951cf40f28297d
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/05/2021
ms.locfileid: "97903979"
---
# <a name="how-to-display-wpf-trace-information"></a>Procedimiento Presentación de información de seguimiento de WPF
[!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] puede recibir información de seguimiento de la depuración de las aplicaciones WPF y mostrar esa información en la ventana **Salida**. Para mostrar la información de seguimiento de depuración, debe estar habilitada la traza de WPF.

 Puede habilitar la traza de WPF en su archivo App.Config o, mediante programación, utilizando la clase <xref:System.Diagnostics.PresentationTraceSources>. Una manera más fácil de habilitar la traza de WPF es usar la ventana **Opciones**. No se admite la traza WPF en las aplicaciones web.

### <a name="to-enable-or-customize-wpf-trace-information"></a>Para habilitar o personalizar la información de seguimiento de WPF

1. En el menú **Herramientas**, seleccione **Opciones**.

2. En el cuadro de diálogo **Opciones**, en el cuadro de la izquierda, abra el nodo **Depuración**.

3. En **Depuración**, haga clic en **Ventana de salida**.

4. En **Configuración general de salida**, seleccione **Toda la salida de depuración**.

5. En el cuadro de la derecha, busque **Configuración de seguimiento de WPF**.

6. Abra el nodo **Configuración de seguimiento de WPF**.

7. En **Configuración de seguimiento de WPF**, haga clic en la categoría de valores que desea habilitar (por ejemplo, **Enlace de datos**).

     Aparecerá un control de lista desplegable en la columna Configuración, al lado de **Enlace de datos** o de la categoría en la que haya hecho clic.

8. Haga clic en la lista desplegable y seleccione el tipo de información de seguimiento que quiere ver: **All**, **Critical**, **Error**, **Warning**, **Information**, **Verbose** o **ActivityTracing**.

     **Critical** solo habilita la traza de los eventos críticos.

     **Error** habilita la traza de los eventos críticos y de error.

     **Warning** habilita la traza de los eventos críticos, de error y de advertencia.

     **Information** habilita la traza de los eventos críticos, de error, de advertencia y de información.

     **Verbose** habilita la traza de los eventos críticos, de error, de advertencia, de información y detallados.

     **ActivityTracing** habilita la traza de los eventos de detención, inicio, suspensión, transferencia y reanudación.

     Para obtener más información sobre el significado de estos niveles de información de seguimiento, vea <xref:System.Diagnostics.SourceLevels>.

9. Haga clic en **Aceptar**.

### <a name="to-disable-wpf-trace-information"></a>Para deshabilitar la información de seguimiento de WPF

1. En el menú **Herramientas**, seleccione **Opciones**.

2. En el cuadro de diálogo **Opciones**, en el cuadro de la izquierda, abra el nodo **Depuración**.

3. En **Depuración**, haga clic en **Ventana de salida**.

4. En el cuadro de la derecha, busque **Configuración de seguimiento de WPF**.

5. Abra el nodo **Configuración de seguimiento de WPF**.

6. En **Configuración de seguimiento de WPF**, haga clic en la categoría de valores que desea habilitar (por ejemplo, **Enlace de datos**).

     Aparecerá un control de lista desplegable en la columna Configuración, al lado de **Enlace de datos** o de la categoría en la que haya hecho clic.

7. Haga clic en la lista desplegable y seleccione **Desactivado**.

8. Haga clic en **Aceptar**.

## <a name="see-also"></a>Vea también
- [Depurar WPF](../debugger/debugging-wpf.md)