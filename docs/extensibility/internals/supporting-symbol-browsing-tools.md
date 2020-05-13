---
title: Compatibilidad con las herramientas de navegación de símbolos ( Symbol-Browsing Tools) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
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
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4998e47ccd6f99df2710833c18975d57e3bb92f5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704767"
---
# <a name="supporting-symbol-browsing-tools"></a>Compatibilidad con herramientas de exploración de símbolos
Las herramientas Examinador de **objetos**, Vista de **clases**, Explorador de **llamadas** y Buscar resultados de **símbolos** proporcionan capacidades de exploración de símbolos en Visual Studio. Estas herramientas muestran vistas jerárquicas de árbol de símbolos y muestran las relaciones entre los símbolos del árbol. Los símbolos pueden representar espacios de nombres, objetos, clases, miembros de clase y otros elementos de lenguaje contenidos en varios componentes. Los componentes incluyen proyectos de Visual Studio, componentes externos de .NET Framework y bibliotecas de tipos (.tlb). Para obtener más información, consulte [Visualización de la estructura de código](../../ide/viewing-the-structure-of-code.md).

## <a name="symbol-browsing-libraries"></a>Bibliotecas de navegación de símbolos
 Como implementador de lenguaje, puede ampliar las capacidades de exploración de símbolos de Visual Studio mediante la creación de bibliotecas que realizan un seguimiento de los símbolos de los componentes y proporcionan las listas de símbolos al Administrador de objetos de Visual Studio a través de un conjunto de interfaces. La interfaz describe <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2> una biblioteca. El Administrador de objetos de Visual Studio responde a las solicitudes de nuevos datos de las herramientas de exploración de símbolos obteniendo los datos de las bibliotecas y organizándolos. Posteriormente rellena o actualiza las herramientas con los datos solicitados. Para obtener una referencia al administrador <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2>de <xref:Microsoft.VisualStudio.Shell.Interop.SVsObjectManager> objetos de `GetService` Visual Studio, , pase el identificador de servicio al método.

 Cada biblioteca debe registrarse con el Administrador de objetos de Visual Studio, que recopila la información de todas las bibliotecas. Para registrar una biblioteca, llame al <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterSimpleLibrary%2A> método. Dependiendo de la herramienta que inicia la solicitud, el Administrador de objetos de Visual Studio busca la biblioteca adecuada y solicita datos. Los datos viajan entre las [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] bibliotecas y el gestor <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2> de objetos en listas de símbolos descritos por la interfaz.

 El [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] administrador de objetos es responsable de actualizar periódicamente las herramientas de exploración de símbolos para reflejar los datos más actuales contenidos en las bibliotecas.

 El diagrama siguiente contiene un ejemplo de elementos clave del proceso de intercambio de solicitudes/datos entre una biblioteca y el administrador de objetos de Visual Studio. Las interfaces del diagrama forman parte de una aplicación de código administrado.

 ![Flujo de datos entre una biblioteca y el administrador de objetos](../../extensibility/internals/media/callbrowserdiagram.gif "CallBrowserDiagram")

 Para proporcionar las listas de símbolos al Administrador de objetos de Visual Studio, <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterSimpleLibrary%2A> primero debe registrar la biblioteca con el Administrador de objetos de Visual Studio llamando al método. Una vez registrada la biblioteca, el Administrador de objetos de Visual Studio solicita cierta información sobre las capacidades de la biblioteca. Por ejemplo, solicita las marcas de biblioteca y <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2.GetLibFlags2%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2.GetSupportedCategoryFields2%2A> las categorías admitidas mediante una llamada a los métodos y. En algún momento, cuando una de las herramientas solicita datos de esta biblioteca, el <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2.GetList2%2A> administrador de objetos solicita la lista de símbolos de nivel superior llamando al método. En respuesta, la biblioteca fabrica una lista de símbolos y la <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2> expone al Administrador de objetos de Visual Studio a través de la interfaz. El [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] administrador de objetos determina cuántos elementos hay en la lista llamando al <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetItemCount%2A> método. Todas las solicitudes siguientes se relacionan con un elemento determinado de la lista y proporcionan el número de índice del elemento en cada solicitud. El Administrador de objetos de Visual Studio procede a recopilar la información sobre el <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetCategoryField2%2A> tipo, la accesibilidad y otras propiedades del elemento mediante una llamada al método.

 Determina el nombre del elemento llamando <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetTextWithOwnership%2A> al método y solicita la <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetDisplayData%2A> información del icono llamando al método. El icono se muestra a la izquierda del nombre del elemento y representa el tipo del elemento, la accesibilidad y otras propiedades.

 El [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] administrador de <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetExpandable3%2A> objetos llama al método para determinar si un elemento de lista determinado se puede expandir y tiene elementos secundarios. Si la interfaz de usuario envía una solicitud para expandir un <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetList2%2A> elemento, el administrador de objetos solicita la lista secundaria de símbolos llamando al método. El proceso continúa con diferentes partes del árbol que se construyen a petición.

> [!NOTE]
> Para implementar un proveedor de <xref:Microsoft.VisualStudio.Shell.Interop.IVsLibrary2> símbolos de código nativo, use las interfaces y. <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectList2>

## <a name="see-also"></a>Vea también
- [Registro de una biblioteca con el Administrador de objetos](../../extensibility/internals/how-to-register-a-library-with-the-object-manager.md)
- [Exposición de listas de símbolos proporcionadas por la biblioteca al Administrador de objetos](../../extensibility/internals/how-to-expose-lists-of-symbols-provided-by-the-library-to-the-object-manager.md)
- [Identificación de símbolos en una biblioteca](../../extensibility/internals/how-to-identify-symbols-in-a-library.md)
