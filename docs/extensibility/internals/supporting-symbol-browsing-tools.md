---
title: "Compatibilidad con herramientas de exploraci&#243;n de s&#237;mbolos | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "símbolos, herramientas de exploración de símbolos"
  - "exploradores, exploradores de símbolos"
  - "herramientas de exploración de símbolos"
  - "bibliotecas"
  - "Interfaz IVsLibrary2, herramientas de exploración de símbolos"
  - "Interfaz IVsSimpleLibrary2, herramientas de exploración de símbolos"
  - "herramientas de exploración de símbolos, Administrador de bibliotecas"
  - "símbolos"
  - "bibliotecas de herramientas de exploración de símbolos"
ms.assetid: 70d8c9e5-4b0b-4a69-b3b3-90f36debe880
caps.latest.revision: 26
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 26
---
# Compatibilidad con herramientas de exploraci&#243;n de s&#237;mbolos
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Las herramientas de**Examinador de objetos**, de **Vista de clases**, de **Explorador de llamadas** y de **Resultados de la búsqueda de símbolos** proporcionan el token que examina funciones en Visual Studio.  Estas herramientas muestran vistas de árbol jerárquicas de símbolos y muestran las relaciones entre los símbolos en el árbol.  Los símbolos pueden representar espacios de nombres, objetos, clases, miembros de clase, y otros elementos del lenguaje contenido en distintos componentes.  Los componentes incluyen los proyectos de Visual Studio, los componentes externos de [!INCLUDE[dnprdnshort](../../code-quality/includes/dnprdnshort_md.md)] y las bibliotecas de tipos \(.tlb\).  Para obtener más información, vea [Ver la estructura del código](../../ide/viewing-the-structure-of-code.md).  
  
## Símbolo\-Examinar bibliotecas  
 Como un implementador de lenguaje, puede ampliar las capacidades símbolo\-que examinan de Visual Studio creando las bibliotecas que siguen los símbolos de los componentes y proporcionan las listas de símbolos al administrador de objetos de Visual Studio a través de un conjunto de interfaces.  Una biblioteca se describe mediante la interfaz de <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2> .  El administrador de objetos de Visual Studio responden a las solicitudes nuevos datos de las herramientas símbolo\-que examinan recopilando datos de bibliotecas y organizarlos.  rellena o actualiza posteriormente las herramientas con los datos solicitados.  Para obtener una referencia al administrador de objetos de Visual Studio, <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2>, pasa el identificador de servicio de <xref:Microsoft.VisualStudio.Shell.Interop.SVsObjectManager> al método de `GetService` .  
  
 Cada biblioteca debe registrar con el administrador de objetos de Visual Studio, que obtiene información sobre todas las bibliotecas.  Para registrar una biblioteca, llame al método de <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterSimpleLibrary%2A> .  Dependiendo de la herramienta inicia la solicitud, el administrador de objetos de Visual Studio busca la biblioteca adecuada y solicita datos.  Los datos se desplaza entre las bibliotecas y el administrador de objetos de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]en listas de símbolos descritos por la interfaz de <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2> .  
  
 El administrador de objetos de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]es responsable periódicamente de actualizar símbolo\-examinando herramientas para reflejar los datos más actuales contenidos en las bibliotecas.  
  
 El diagrama siguiente contiene un ejemplo de los elementos clave de solicitudes\/proceso de intercambio de datos entre una biblioteca y el administrador de objetos de Visual Studio.  Interfaces del diagrama son parte de una aplicación de código administrado.  
  
 ![Flujo de datos entre una biblioteca y el administrador de objetos](~/extensibility/internals/media/callbrowserdiagram.gif "CallBrowserDiagram")  
  
 Para proporcionar listas de símbolos al administrador de objetos de Visual Studio, debe registrar primero la biblioteca con el administrador de objetos de Visual Studio llamando al método <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterSimpleLibrary%2A> .  Una vez registrado la biblioteca, el administrador de objetos de Visual Studio solicita cierta información sobre las funciones de la biblioteca.  Por ejemplo, solicita los marcadores de la biblioteca y categorías compatibles llamando a los métodos de <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2.GetLibFlags2%2A> y de <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2.GetSupportedCategoryFields2%2A> .  En algún punto, cuando una de las herramientas solicita datos de esta biblioteca, el administrador de objetos solicita la lista de nivel superior de símbolos llamando al método <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2.GetList2%2A> .  En respuesta, la biblioteca produce una lista de símbolos y la expone el administrador de objetos de Visual Studio a través de la interfaz de <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2> .  El administrador de objetos de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]determina cuántos elementos están en la lista llamando al método de <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetItemCount%2A> .  Todas las solicitudes de siguiente se relacionan con un elemento determinado en la lista y escriba el número de índice del elemento en cada solicitud.  El administrador de objetos de Visual Studio continúa para obtener la información del tipo, la accesibilidad, y otras propiedades del elemento llamando al método <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetCategoryField2%2A> .  
  
 Determina el nombre del elemento llamando al método <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetTextWithOwnership%2A> y solicita información de icono llamando al método <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetDisplayData%2A> .  El icono se muestra a la izquierda del nombre de elemento y describe el tipo de elemento, de accesibilidad, y otras propiedades.  
  
 El administrador de objetos de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] llama al método de <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetExpandable3%2A> para determinar si un elemento de lista especificado es expansible y tiene elementos secundarios los elementos.  Si la interfaz de usuario envía una solicitud para expandir un elemento, el administrador de objetos solicita la lista secundaria de símbolos llamando al método <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetList2%2A> .  El proceso continúa con partes diferentes del árbol que se compila a petición.  
  
> [!NOTE]
>  Para implementar un proveedor de token de código nativo, use las interfaces de <xref:Microsoft.VisualStudio.Shell.Interop.IVsLibrary2> y de <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectList2> .  
  
## Vea también  
 [Cómo: registrar una biblioteca con el Administrador de objetos](../../extensibility/internals/how-to-register-a-library-with-the-object-manager.md)   
 [Cómo: exponer listas de símbolos proporcionadas por la biblioteca al administrador de objetos](../../extensibility/internals/how-to-expose-lists-of-symbols-provided-by-the-library-to-the-object-manager.md)   
 [Cómo: identificar símbolos en una biblioteca](../../extensibility/internals/how-to-identify-symbols-in-a-library.md)