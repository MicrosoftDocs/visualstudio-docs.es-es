---
title: Información de parámetros en un archivo de lenguaje heredado1 | Documentos de Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services, method tips
- method tips
- language services, parameter info tooltip
- IVsMethodData interface
- Parameter Info (IntelliSense)
ms.assetid: f367295e-45b6-45d2-9ec8-77481743beef
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 715de0c8ac763a8aa307fcf31038ba1b60c359fd
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53864461"
---
# <a name="parameter-info-in-a-legacy-language-service"></a>Información de parámetros en un servicio de lenguaje heredado
La información sobre herramientas de información de parámetros IntelliSense proporciona a los usuarios con sugerencias sobre dónde se encuentra en una construcción de lenguaje.  
  
 Servicios de lenguaje heredado se implementan como parte de un paquete VSPackage, pero la forma más reciente para implementar características de servicio de lenguaje es usar las extensiones MEF. Para obtener más información, consulte [ampliación del Editor y los servicios de lenguaje](../../extensibility/extending-the-editor-and-language-services.md).  
  
> [!NOTE]
>  Se recomienda que comience a usar el nuevo editor de API tan pronto como sea posible. Esto mejorará el rendimiento de su servicio de lenguaje y le permiten aprovechar las nuevas características del editor.  
  
## <a name="how-parameter-info-tooltips-work"></a>Cómo funciona el parámetro información sobre herramientas  
 Cuando se escribe una instrucción en el editor, el VSPackage muestra una ventana pequeña información sobre herramientas que contiene la definición de la instrucción que se ha escrito. Por ejemplo, si escribe una instrucción de Microsoft Foundation Classes (MFC) (como `pMainFrame ->UpdateWindow`) y presione el paréntesis de apertura de clave para empezar a enumerar los parámetros, una sugerencia de método aparece muestra la definición de la `UpdateWindow` método.  
  
 Parámetro información sobre herramientas se utiliza normalmente junto con la finalización de instrucciones. Son más útiles para los lenguajes que tienen parámetros u otra información con formato después de la palabra clave o el nombre del método.  
  
 La información de parámetros, información sobre herramientas se inician mediante el servicio de lenguaje a través de la intercepción de comandos. Para interceptar los caracteres de usuario, debe implementar el objeto de servicio de lenguaje el <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfaz y la vista de texto puede pasar un puntero a su <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> implementación, mediante una llamada a la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> método en el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> interfaz. El filtro de comandos intercepta comandos que se escribe en la ventana de código. Supervisar la información de comandos para saber cuándo se debe mostrar la información de parámetros al usuario. Puede usar el mismo filtro de comando para la finalización de instrucciones, los marcadores de error y así sucesivamente.  
  
 Cuando se escribe una palabra clave para el que el servicio de lenguaje puede proporcionar sugerencias, a continuación, el servicio de lenguaje crea una <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow> objeto y llama a la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateTipWindow%2A> método en el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> interfaz para notificar el IDE para mostrar una sugerencia. Crear el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow> objeto `VSLocalCreateInstance` y especificando la coclase `CLSID_VsMethodTipWindow`. `VsLocalCreateInstance` es una función definida en el vsdoc.h del archivo de encabezado que llama a `QueryService` para el registro local y la llama `CreateInstance` en este objeto para el `CLSID_VsMethodTipWindow`.  
  
## <a name="providing-a-method-tip"></a>Proporcionar una sugerencia de método  
 Para proporcionar una sugerencia de método, llame a la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow.SetMethodData%2A> método en el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow> interfaz, pasándole la implementación de la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData> interfaz.  
  
 Cuando su <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData> se invoca la clase, sus métodos se llaman en el orden siguiente:  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetContextStream%2A>  
  
     Devuelve la posición y longitud de los datos relevantes en el búfer de texto actual. Esto indica al IDE que no oculte esos datos con la ventana de información sobre herramientas.  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetCurMethod%2A>  
  
     Devuelve el número del método (índice de base cero) que desea que se muestre inicialmente. Por ejemplo, si se devuelve cero, inicialmente se presenta el primer método sobrecargado.  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetOverloadCount%2A>  
  
     Devuelve el número de métodos sobrecargados que son aplicables en el contexto actual. Si devuelve un valor mayor que 1 para este método, a continuación, la vista de texto muestra flechas arriba y abajo para usted. Si hace clic en la flecha hacia abajo, el IDE llama el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.NextMethod%2A> método. Si hace clic en la flecha hacia arriba, el IDE llama el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.PrevMethod%2A> método.  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetMethodText%2A>  
  
     El texto de la información de parámetros, información sobre herramientas se construye durante varias llamadas a la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetMethodText%2A> y <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetParameterText%2A> métodos.  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetParameterCount%2A>  
  
     Devuelve el número de parámetros que se muestra en el método.  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetParameterText%2A>  
  
     Si devuelve un número del método correspondiente con la sobrecarga que desea mostrar, se llama a este método, seguido por una llamada a la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.UpdateView%2A> método.  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.UpdateView%2A>  
  
     Informa a su servicio de lenguaje para actualizar el editor cuando se muestra una sugerencia de método. En el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.UpdateView%2A> método, llame a lo siguiente:  
  
    ```  
    <pTxWin> ->UpdateTipWindow(<pTip>, UTW_CONTENTCHANGED | UTW_CONTEXTCHANGED).  
    ```  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A>  
  
     Recibir una llamada a la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A> al cerrar la ventana de sugerencia de método.