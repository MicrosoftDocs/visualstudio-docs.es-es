---
title: Información de parámetros en un lenguaje antiguo Service1 | Microsoft Docs
description: Obtenga información sobre cómo implementar la información sobre parámetros de IntelliSense información sobre herramientas, que proporciona a los usuarios sugerencias, en un servicio de lenguaje heredado.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services, method tips
- method tips
- language services, parameter info tooltip
- IVsMethodData interface
- Parameter Info (IntelliSense)
ms.assetid: f367295e-45b6-45d2-9ec8-77481743beef
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0cd49644e670df42f4630af987a5e9152b4f6c95
ms.sourcegitcommit: 0c9155e9b9408fb7481d79319bf08650b610e719
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/05/2021
ms.locfileid: "97876810"
---
# <a name="parameter-info-in-a-legacy-language-service-1"></a>Información de parámetros en un servicio de lenguaje heredado 1
La información sobre parámetros de IntelliSense proporciona a los usuarios sugerencias sobre dónde se encuentran en una construcción de lenguaje.

 Los servicios de lenguaje heredados se implementan como parte de un VSPackage, pero la forma más reciente de implementar las características del servicio de lenguaje es usar extensiones de MEF. Para obtener más información, vea [extender el editor y los servicios de lenguaje](../../extensibility/extending-the-editor-and-language-services.md).

> [!NOTE]
> Le recomendamos que empiece a usar la nueva API del editor lo antes posible. Esto mejorará el rendimiento del servicio de lenguaje y le permitirá aprovechar las nuevas características del editor.

## <a name="how-parameter-info-tooltips-work"></a>Cómo funcionan la información sobre herramientas de información de parámetros
 Al escribir una instrucción en el editor, el VSPackage muestra una pequeña ventana de información sobre herramientas que contiene la definición de la instrucción que se va a escribir. Por ejemplo, si escribe una instrucción Microsoft Foundation Classes (MFC) (como `pMainFrame ->UpdateWindow` ) y presiona la tecla de paréntesis de apertura para empezar a enumerar los parámetros, aparece una sugerencia de método que muestra la definición del `UpdateWindow` método.

 Información sobre parámetros la información sobre herramientas se usa normalmente junto con la finalización de instrucciones. Son muy útiles para los lenguajes que tienen parámetros u otra información con formato después del nombre del método o la palabra clave.

 El servicio de lenguaje inicia la información sobre herramientas información de parámetros a través de la interceptación de comandos. Para interceptar los caracteres de usuario, el objeto de servicio de lenguaje debe implementar la <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfaz y pasar a la vista de texto un puntero a la <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> implementación, llamando al <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> método en la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> interfaz. El filtro de comandos intercepta los comandos que se escriben en la ventana de código. Supervise la información del comando para saber cuándo se debe mostrar la información de parámetros al usuario. Puede usar el mismo filtro de comandos para la finalización de instrucciones, los marcadores de error, etc.

 Cuando se escribe una palabra clave para la que el servicio de lenguaje puede proporcionar sugerencias, el servicio de lenguaje crea un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow> objeto y llama al <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateTipWindow%2A> método en la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> interfaz para notificar al IDE que debe mostrar una sugerencia. Cree el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow> objeto usando `VSLocalCreateInstance` y especificando la coclase `CLSID_VsMethodTipWindow` . `VsLocalCreateInstance` es una función definida en el archivo de encabezado vsdoc. h que llama al `QueryService` registro local y llama a `CreateInstance` en este objeto para `CLSID_VsMethodTipWindow` .

## <a name="providing-a-method-tip"></a>Proporcionar una sugerencia de método
 Para proporcionar una sugerencia de método, llame al <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow.SetMethodData%2A> método en la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow> interfaz, pasándole su implementación de la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData> interfaz.

 Cuando <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData> se invoca la clase, se llama a sus métodos en el orden siguiente:

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetContextStream%2A>

     Devuelve la posición y la longitud de los datos pertinentes en el búfer de texto actual. Esto indica al IDE que no oculte esos datos con la ventana de información sobre herramientas.

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetCurMethod%2A>

     Devuelve el número de método (índice basado en cero) que desea que se muestre inicialmente. Por ejemplo, si devuelve cero, se presenta inicialmente el primer método sobrecargado.

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetOverloadCount%2A>

     Devuelve el número de métodos sobrecargados que se aplican en el contexto actual. Si devuelve un valor mayor que 1 para este método, la vista de texto muestra flechas arriba y abajo. Si hace clic en la flecha hacia abajo, el IDE llama al <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.NextMethod%2A> método. Si hace clic en la flecha arriba, el IDE llama al <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.PrevMethod%2A> método.

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetMethodText%2A>

     El texto de la información de parámetros información sobre herramientas se construye durante varias llamadas a los <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetMethodText%2A> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetParameterText%2A> métodos y.

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetParameterCount%2A>

     Devuelve el número de parámetros que se van a mostrar en el método.

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetParameterText%2A>

     Si devuelve un número de método correspondiente a la sobrecarga que desea mostrar, se llama a este método, seguido de una llamada al <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.UpdateView%2A> método.

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.UpdateView%2A>

     Informa a su servicio de lenguaje para actualizar el editor cuando se muestra una sugerencia de método. En el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.UpdateView%2A> método, llame a lo siguiente:

    ```
    <pTxWin> ->UpdateTipWindow(<pTip>, UTW_CONTENTCHANGED | UTW_CONTEXTCHANGED).
    ```

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A>

     Recibirá una llamada al <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A> método al cerrar la ventana de la sugerencia de método.
