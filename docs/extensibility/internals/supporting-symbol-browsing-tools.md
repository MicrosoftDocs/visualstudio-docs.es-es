---
title: Compatibilidad con herramientas de Symbol-Browsing | Microsoft Docs
description: Visual Studio proporciona funciones de exploración de símbolos en Visual Studio. Obtenga información sobre cómo ampliar estas capacidades con bibliotecas para los símbolos de los componentes.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 0adf586831e21c2448931215d4ef4a89d16a63f8
ms.sourcegitcommit: 0c9155e9b9408fb7481d79319bf08650b610e719
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/05/2021
ms.locfileid: "97876446"
---
# <a name="supporting-symbol-browsing-tools"></a>Compatibilidad con herramientas de exploración de símbolos
Las herramientas **Examinador de objetos**, **vista de clases**, **Explorador de llamadas** y **Buscar resultados de símbolos** proporcionan funciones de exploración de símbolos en Visual Studio. Estas herramientas muestran vistas de árbol jerárquicas de símbolos y muestran las relaciones entre los símbolos del árbol. Los símbolos pueden representar espacios de nombres, objetos, clases, miembros de clase y otros elementos de lenguaje contenidos en varios componentes. Los componentes incluyen proyectos de Visual Studio, componentes de .NET Framework externos y bibliotecas de tipo (. tlb). Para obtener más información, vea [ver la estructura del código](../../ide/viewing-the-structure-of-code.md).

## <a name="symbol-browsing-libraries"></a>Bibliotecas de Symbol-Browsing
 Como implementador de lenguaje, puede ampliar las funcionalidades de exploración de símbolos de Visual Studio mediante la creación de bibliotecas que realizan el seguimiento de los símbolos de los componentes y proporcionan listas de símbolos al administrador de objetos de Visual Studio a través de un conjunto de interfaces. Una biblioteca se describe mediante la <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2> interfaz. El administrador de objetos de Visual Studio responde a las solicitudes de datos nuevos de las herramientas de exploración de símbolos mediante la obtención de los datos de las bibliotecas y su organización. Posteriormente, rellenará o actualizará las herramientas con los datos solicitados. Para obtener una referencia al administrador de objetos de Visual Studio, <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2> , pase el <xref:Microsoft.VisualStudio.Shell.Interop.SVsObjectManager> identificador de servicio al `GetService` método.

 Cada biblioteca se debe registrar con el administrador de objetos de Visual Studio, que recopila la información de todas las bibliotecas. Para registrar una biblioteca, llame al <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterSimpleLibrary%2A> método. En función de la herramienta que inicia la solicitud, el administrador de objetos de Visual Studio busca la biblioteca adecuada y solicita los datos. Los datos viajan entre las bibliotecas y el [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Administrador de objetos en las listas de símbolos descritos por la <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2> interfaz.

 El [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Administrador de objetos es responsable de actualizar periódicamente las herramientas de exploración de símbolos para reflejar los datos más actuales contenidos en las bibliotecas.

 El diagrama siguiente contiene un ejemplo de elementos clave del proceso de intercambio de solicitudes y datos entre una biblioteca y el administrador de objetos de Visual Studio. Las interfaces del diagrama forman parte de una aplicación de código administrado.

 ![Flujo de datos entre una biblioteca y el administrador de objetos](../../extensibility/internals/media/callbrowserdiagram.gif "CallBrowserDiagram")

 Para proporcionar las listas de símbolos al administrador de objetos de Visual Studio, primero debe registrar la biblioteca con el administrador de objetos de Visual Studio llamando al <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterSimpleLibrary%2A> método. Una vez registrada la biblioteca, el administrador de objetos de Visual Studio solicita cierta información acerca de las capacidades de la biblioteca. Por ejemplo, solicita las marcas de biblioteca y las categorías admitidas llamando a los <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2.GetLibFlags2%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2.GetSupportedCategoryFields2%2A> métodos y. En algún momento, cuando una de las herramientas solicita datos de esta biblioteca, el administrador de objetos solicita la lista de nivel superior de símbolos mediante una llamada al <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2.GetList2%2A> método. En respuesta, la biblioteca fabrica una lista de símbolos y lo expone al administrador de objetos de Visual Studio a través de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2> interfaz. El [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Administrador de objetos determina el número de elementos que hay en la lista mediante una llamada al <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetItemCount%2A> método. Todas las solicitudes siguientes se relacionan con un elemento determinado de la lista y proporcionan el número de índice del elemento en cada solicitud. El administrador de objetos de Visual Studio continúa recopilando la información sobre el tipo, la accesibilidad y otras propiedades del elemento llamando al <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetCategoryField2%2A> método.

 Determina el nombre del elemento llamando al <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetTextWithOwnership%2A> método y solicita la información del icono mediante una llamada al <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetDisplayData%2A> método. El icono se muestra a la izquierda del nombre del elemento y describe el tipo del elemento, la accesibilidad y otras propiedades.

 El [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Administrador de objetos llama al <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetExpandable3%2A> método para determinar si un elemento de lista determinado es expansible y tiene elementos secundarios. Si la interfaz de usuario envía una solicitud para expandir un elemento, el administrador de objetos solicita la lista de símbolos secundarias llamando al <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetList2%2A> método. El proceso continúa con diferentes partes del árbol que se están generando a petición.

> [!NOTE]
> Para implementar un proveedor de símbolos de código nativo, use las <xref:Microsoft.VisualStudio.Shell.Interop.IVsLibrary2> <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectList2> interfaces y.

## <a name="see-also"></a>Consulte también
- [Registro de una biblioteca con el Administrador de objetos](../../extensibility/internals/how-to-register-a-library-with-the-object-manager.md)
- [Exposición de listas de símbolos proporcionadas por la biblioteca al Administrador de objetos](../../extensibility/internals/how-to-expose-lists-of-symbols-provided-by-the-library-to-the-object-manager.md)
- [Identificación de símbolos en una biblioteca](../../extensibility/internals/how-to-identify-symbols-in-a-library.md)
