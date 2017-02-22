---
title: "Informaci&#243;n de par&#225;metros en un servicio de lenguaje heredado | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Servicios de lenguaje, sugerencias (método)"
  - "sugerencias (método)"
  - "Servicios de lenguaje, parámetro información rápida sobre herramientas"
  - "Interfaz IVsMethodData"
  - "Información de parámetros (IntelliSense)"
ms.assetid: f367295e-45b6-45d2-9ec8-77481743beef
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# Informaci&#243;n de par&#225;metros en un servicio de lenguaje heredado
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

La información de parámetros de IntelliSense, información sobre herramientas proporciona a los usuarios con sugerencias sobre dónde se encuentra en una construcción de lenguaje.  
  
 Servicios de lenguaje heredado se implementan como parte de un paquete VSPackage, pero la nueva forma de implementar las características del servicio de lenguaje es usar extensiones MEF. Para obtener más información, consulte [Extender el Editor y los servicios de lenguaje](../../extensibility/extending-the-editor-and-language-services.md).  
  
> [!NOTE]
>  Se recomienda que comience a utilizar el nuevo editor de API tan pronto como sea posible. Esto mejora el rendimiento de su servicio de lenguaje y le permiten aprovechar las nuevas características del editor.  
  
## Cómo funciona los parámetro información sobre herramientas  
 Cuando se escribe una instrucción en el editor, el VSPackage muestra una ventana pequeña de información sobre herramientas que contiene la definición de la instrucción que se ha escrito. Por ejemplo, si escribe una instrucción de Microsoft Foundation Classes \(MFC\) \(como `pMainFrame ->UpdateWindow`\) y presione el paréntesis de apertura de clave para empezar a enumerar parámetros, aparece una sugerencia para método muestra la definición de la `UpdateWindow` \(método\).  
  
 Parámetro información sobre herramientas se utiliza normalmente junto con la finalización de instrucciones. Son más útiles para los lenguajes que tienen parámetros u otra información con formato después de la palabra clave o el nombre del método.  
  
 El parámetro informaciones iniciadas por el servicio de lenguaje a través de intercepción de comandos. Para interceptar los caracteres de usuario, debe implementar el objeto de servicio de lenguaje el <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> de interfaz y la vista de texto puede pasar un puntero a su <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> implementación, llamando a la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> método en el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> interfaz. El filtro de comandos intercepta los comandos que se escriben en la ventana de código. Supervisar la información del comando para saber cuándo se debe mostrar la información de parámetros al usuario. Puede usar el mismo filtro de comando para la finalización de instrucciones, los marcadores de error y así sucesivamente.  
  
 Cuando se escribe una palabra clave para la que el servicio de lenguaje puede proporcionar sugerencias, el servicio de lenguaje crea un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow> objeto y llama el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateTipWindow%2A> método en el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> interfaz para notificar el IDE para mostrar una sugerencia. Crear la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow> objeto mediante `VSLocalCreateInstance` y especificando la coclase `CLSID_VsMethodTipWindow`.`VsLocalCreateInstance` es una función definida en el vsdoc.h del archivo de encabezado que llama a `QueryService` para el registro local y llama `CreateInstance` en este objeto para el `CLSID_VsMethodTipWindow`.  
  
## Proporciona una sugerencia \(método\)  
 Para proporcionar una sugerencia de método, llame a la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow.SetMethodData%2A> método en el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow> interfaz, pasando la implementación de la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData> interfaz.  
  
 Cuando su <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData> se invoca la clase, se llaman a sus métodos en el orden siguiente:  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetContextStream%2A>  
  
     Devuelve la posición y longitud de los datos relevantes en el búfer de texto actual. Esto indica que el IDE para no interferir con esos datos con la ventana de información sobre herramientas.  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetCurMethod%2A>  
  
     Devuelve el número de método \(índice de base cero\) que desea que se muestre inicialmente. Por ejemplo, si se devuelve cero, inicialmente se presenta el primer método sobrecargado.  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetOverloadCount%2A>  
  
     Devuelve el número de métodos sobrecargados que son aplicables en el contexto actual. Si se devuelve un valor mayor que 1 para este método, a continuación, la vista de texto muestra flechas arriba y abajo para usted. Si hace clic en la flecha hacia abajo, el IDE llama el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.NextMethod%2A> método. Si hace clic en la flecha arriba, el IDE llama el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.PrevMethod%2A> método.  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetMethodText%2A>  
  
     El texto de la información de parámetros, información sobre herramientas se construye durante varias llamadas a la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetMethodText%2A> y <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetParameterText%2A> métodos.  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetParameterCount%2A>  
  
     Devuelve el número de parámetros para mostrar en el método.  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetParameterText%2A>  
  
     Si devuelve un número de método correspondiente con la sobrecarga que desea mostrar, se llama a este método, seguido por una llamada a la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.UpdateView%2A> \(método\).  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.UpdateView%2A>  
  
     Informa al servicio de lenguaje para actualizar el editor cuando se muestra una sugerencia de método. En el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.UpdateView%2A> método, llame a lo siguiente:  
  
    ```  
    <pTxWin> ->UpdateTipWindow(<pTip>, UTW_CONTENTCHANGED | UTW_CONTEXTCHANGED).  
    ```  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A>  
  
     Recibe una llamada a la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A> método cuando se cierra la ventana de sugerencia de método.