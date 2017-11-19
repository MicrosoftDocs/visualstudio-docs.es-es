---
title: "Compatibilidad con herramientas de exploración de símbolo | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- symbols, symbol-browsing tools
- browsers, symbol browsers
- symbol-browsing tools
- libraries
- IVsLibrary2 interface, symbol-browsing tools
- IVsSimpleLibrary2 interface, symbol-browsing tools
- symbol-browsing tools, library manager
- symbols
- libraries, symbol-browsing tools
ms.assetid: 70d8c9e5-4b0b-4a69-b3b3-90f36debe880
caps.latest.revision: "26"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 9b9e9963b43e6ca2049337fdfdf76b0a1314ae32
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="supporting-symbol-browsing-tools"></a>Compatibilidad con herramientas de exploración de símbolos
**Examinador de objetos**, **vista de clases**, **Examinador de llamadas** y **resultados de la búsqueda de símbolos** herramientas proporcionan símbolos examinar funciones en Visual Studio. Estas herramientas muestran vistas de árbol jerárquico de símbolos y mostrar las relaciones entre los símbolos en el árbol. Pueden representar los símbolos de espacios de nombres, objetos, clases, miembros de clase y otros elementos de lenguaje incluidos en varios componentes. Los componentes incluyen proyectos de Visual Studio, externos [!INCLUDE[dnprdnshort](../../code-quality/includes/dnprdnshort_md.md)] componentes y las bibliotecas de tipos (.tlb). Para obtener más información, vea [Ver la estructura del código](../../ide/viewing-the-structure-of-code.md).  
  
## <a name="symbol-browsing-libraries"></a>Bibliotecas de exploración de símbolos  
 Como un implementador de idioma, puede ampliar las capacidades de exploración de símbolos de Visual Studio mediante la creación de las bibliotecas que realizar un seguimiento de los símbolos de los componentes y proporcionan las listas de símbolos para el Administrador de objetos de Visual Studio a través de un conjunto de las interfaces. Describe una biblioteca de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2> interfaz. El Administrador de objetos de Visual Studio responde a solicitudes para los nuevos datos de las herramientas de exploración de símbolos obteniendo los datos de las bibliotecas y su organización. Posteriormente se rellenan o se actualiza las herramientas con los datos solicitados. Para obtener una referencia al administrador de objetos de Visual Studio, <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2>, pasar la <xref:Microsoft.VisualStudio.Shell.Interop.SVsObjectManager> servicio Id. para el `GetService` método.  
  
 Cada biblioteca debe registrar con el Administrador de objetos de Visual Studio, que recopila la información en todas las bibliotecas. Para registrar una biblioteca, llame a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterSimpleLibrary%2A> método. Dependiendo de la herramienta que inicia la solicitud, el Administrador de objetos de Visual Studio busca la biblioteca adecuada y solicita los datos. Los datos se transfieren entre las bibliotecas y el [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] el Administrador de objetos en listas de símbolos descritos por el <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2> interfaz.  
  
 El [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] el Administrador de objetos es responsable de actualizar periódicamente herramientas de exploración de símbolo para reflejar los datos más recientes contenidos en las bibliotecas.  
  
 El diagrama siguiente contiene un ejemplo de los elementos clave del proceso de intercambio de solicitudes/datos entre una biblioteca y el Administrador de objetos de Visual Studio. Las interfaces en el diagrama forman parte de una aplicación de código administrado.  
  
 ![Flujo de datos entre una biblioteca y el Administrador de objetos](../../extensibility/internals/media/callbrowserdiagram.gif "CallBrowserDiagram")  
  
 Para proporcionar las listas de símbolos para el Administrador de objetos de Visual Studio, en primer lugar debe registrar la biblioteca con el Administrador de objetos de Visual Studio mediante una llamada a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterSimpleLibrary%2A> método. Cuando se registre la biblioteca, el Administrador de objetos de Visual Studio solicita determinada información acerca de las capacidades de la biblioteca. Por ejemplo, se solicita a los marcadores de biblioteca y admite categorías mediante una llamada a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2.GetLibFlags2%2A> y <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2.GetSupportedCategoryFields2%2A> métodos. En algún momento, cuando una de las herramientas solicita datos de esta biblioteca, el Administrador de objetos solicita la lista de símbolos de nivel superior mediante una llamada a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2.GetList2%2A> método. En respuesta, la biblioteca fabrica una lista de símbolos y expone para el Administrador de objetos de Visual Studio a través de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2> interfaz. El [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] el Administrador de objetos determina el número de elementos que está en la lista mediante una llamada a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetItemCount%2A> método. Todas las solicitudes siguientes se relacionan con un elemento determinado en la lista y proporcionan el número de índice del elemento en cada solicitud. El Administrador de objetos de Visual Studio avanza a recopilar la información en el tipo, la accesibilidad y otras propiedades del elemento mediante una llamada a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetCategoryField2%2A> método.  
  
 Determina el nombre del elemento mediante una llamada a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetTextWithOwnership%2A> método y solicita la información de icono mediante una llamada a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetDisplayData%2A> método. El icono se muestra a la izquierda del nombre del elemento y describe el tipo de elemento, la accesibilidad y otras propiedades.  
  
 El [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] objeto llamadas del Administrador de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetExpandable3%2A> método para determinar si un elemento de lista determinado es expansible y tiene los elementos secundarios. Si la interfaz de usuario envía una solicitud para expandir un elemento, el Administrador de objetos solicita la lista secundaria de símbolos mediante una llamada a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetList2%2A> método. El proceso continúa con diferentes partes del árbol que se está generando a petición.  
  
> [!NOTE]
>  Para implementar un proveedor de símbolos de código nativo, use la <xref:Microsoft.VisualStudio.Shell.Interop.IVsLibrary2> y <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectList2> interfaces.  
  
## <a name="see-also"></a>Vea también  
 [Cómo: registrar una biblioteca con el Administrador de objetos](../../extensibility/internals/how-to-register-a-library-with-the-object-manager.md)   
 [Cómo: exponer listas de símbolos proporcionadas por la biblioteca en el Administrador de objetos](../../extensibility/internals/how-to-expose-lists-of-symbols-provided-by-the-library-to-the-object-manager.md)   
 [Identificación de símbolos en una biblioteca](../../extensibility/internals/how-to-identify-symbols-in-a-library.md)