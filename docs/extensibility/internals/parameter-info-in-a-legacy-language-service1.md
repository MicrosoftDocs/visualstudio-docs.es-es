---
title: Información de parámetros en un servicio de lenguaje heredado1 Microsoft Docs
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
ms.openlocfilehash: c26073252aae5434ba5a8197955948d0d9ec883d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706803"
---
# <a name="parameter-info-in-a-legacy-language-service"></a>Información de parámetros en un servicio de lenguaje heredado
La información sobre parámetros de IntelliSense proporciona a los usuarios sugerencias sobre dónde se encuentran en una construcción de lenguaje.

 Los servicios de lenguaje heredados se implementan como parte de un VSPackage, pero la forma más reciente de implementar características de servicio de lenguaje es usar extensiones MEF. Para obtener más información, consulte [Ampliación del editor y](../../extensibility/extending-the-editor-and-language-services.md)los servicios de lenguaje .

> [!NOTE]
> Le recomendamos que comience a usar la nueva API del editor lo antes posible. Esto mejorará el rendimiento de su servicio de lenguaje y le permitirá aprovechar las nuevas características del editor.

## <a name="how-parameter-info-tooltips-work"></a>Cómo funcionan las descripciones emergentes de información de parámetros
 Al escribir una instrucción en el editor, el VSPackage muestra una pequeña ventana de información sobre herramientas que contiene la definición de la instrucción que se escribe. Por ejemplo, si escribe una instrucción Microsoft Foundation `pMainFrame ->UpdateWindow`Classes (MFC) (como ) y presiona la tecla de paréntesis `UpdateWindow` de apertura para comenzar a enumerar los parámetros, aparece una sugerencia de método que muestra la definición del método.

 Las descripciones emergentes de información de parámetros se suelen utilizar junto con la finalización de instrucciones. Son más útiles para los idiomas que tienen parámetros u otra información formateada después del nombre del método o la palabra clave.

 La información de parámetros se inicia mediante el servicio de lenguaje a través de la interceptación de comandos. Para interceptar caracteres de usuario, <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> el objeto de servicio de <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> lenguaje debe <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> implementar la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> interfaz y pasar la vista de texto un puntero a la implementación, llamando al método en la interfaz. El filtro de comandos intercepta los comandos que escriba en la ventana de código. Supervise la información del comando para saber cuándo mostrar información de parámetros al usuario. Puede utilizar el mismo filtro de comandos para la finalización de instrucciones, marcadores de error, etc.

 Al escribir una palabra clave para la que el servicio <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow> de lenguaje <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateTipWindow%2A> puede proporcionar <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> sugerencias, el servicio de lenguaje crea un objeto y llama al método en la interfaz para notificar al IDE para mostrar una sugerencia. Cree <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow> el `VSLocalCreateInstance` objeto utilizando y `CLSID_VsMethodTipWindow`especificando la coclase . `VsLocalCreateInstance`es una función definida en el archivo `QueryService` de encabezado vsdoc.h que llama al registro local y llama `CreateInstance` a este objeto para el `CLSID_VsMethodTipWindow`archivo .

## <a name="providing-a-method-tip"></a>Proporcionar una sugerencia de método
 Para proporcionar una sugerencia <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow.SetMethodData%2A> de método, llame al método en la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow> interfaz, pasándole la implementación de la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData> interfaz.

 Cuando <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData> se invoca la clase, se llama a sus métodos en el siguiente orden:

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetContextStream%2A>

     Devuelve la posición y la longitud de los datos relevantes en el búfer de texto actual. Esto indica al IDE que no oscurezca esos datos con la ventana de información sobre herramientas.

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetCurMethod%2A>

     Devuelve el número de método (índice de base cero) que desea que se muestre inicialmente. Por ejemplo, si devuelve cero, se presenta inicialmente el primer método sobrecargado.

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetOverloadCount%2A>

     Devuelve el número de métodos sobrecargados que son aplicables en el contexto actual. Si devuelve un valor mayor que 1 para este método, la vista de texto muestra las flechas arriba y abajo. Si hace clic en la flecha <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.NextMethod%2A> hacia abajo, el IDE llama al método. Si hace clic en la flecha <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.PrevMethod%2A> hacia arriba, el IDE llama al método.

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetMethodText%2A>

     El texto de la información de parámetros <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetMethodText%2A> información <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetParameterText%2A> sobre herramientas se construye durante varias llamadas a los métodos y.

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetParameterCount%2A>

     Devuelve el número de parámetros que se mostrarán en el método.

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetParameterText%2A>

     Si devuelve un número de método correspondiente a la sobrecarga que desea mostrar, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.UpdateView%2A> se llama a este método, seguido de una llamada al método.

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.UpdateView%2A>

     Informa al servicio de lenguaje para actualizar el editor cuando se muestra una sugerencia de método. En <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.UpdateView%2A> el método, llame a lo siguiente:

    ```
    <pTxWin> ->UpdateTipWindow(<pTip>, UTW_CONTENTCHANGED | UTW_CONTEXTCHANGED).
    ```

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A>

     Recibirá una llamada <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A> al método al cerrar la ventana de sugerencia del método.
