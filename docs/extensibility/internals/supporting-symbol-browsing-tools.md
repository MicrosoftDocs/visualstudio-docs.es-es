---
title: Herramientas de exploración de símbolos de compatibilidad | Documentos de Microsoft
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
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 649ba0583a70d0d53d8b12f26573daf3c52cf5e9
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "66331201"
---
# <a name="supporting-symbol-browsing-tools"></a>Compatibilidad con herramientas de exploración de símbolos
**Examinador de objetos**, **vista de clases**, **Examinador de llamadas** y **resultados de la búsqueda de símbolos** herramientas proporcionan capacidades en Visual Studio de exploración de símbolos. Estas herramientas mostrar vistas de árbol jerárquico de símbolos y mostrar las relaciones entre los símbolos en el árbol. Pueden representar los símbolos de espacios de nombres, objetos, clases, miembros de clase y otros elementos de lenguaje contenidas en varios componentes. Los componentes incluyen los proyectos de Visual Studio, externos [!INCLUDE[dnprdnshort](../../code-quality/includes/dnprdnshort_md.md)] componentes y bibliotecas de tipos (.tlb). Para obtener más información, vea [Ver la estructura del código](../../ide/viewing-the-structure-of-code.md).

## <a name="symbol-browsing-libraries"></a>Bibliotecas de exploración de símbolos
 Como implementador de un idioma, puede ampliar las capacidades de exploración de símbolos de Visual Studio mediante la creación de bibliotecas que realizar un seguimiento de los símbolos de los componentes y proporcionan las listas de símbolos para el Administrador de objetos de Visual Studio a través de un conjunto de las interfaces. Se describe una biblioteca mediante el <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2> interfaz. El Administrador de objetos de Visual Studio responde a solicitudes para los nuevos datos desde las herramientas de exploración de símbolos mediante la obtención de los datos de las bibliotecas y su organización. Posteriormente se rellena o se actualiza las herramientas con los datos solicitados. Para obtener una referencia al administrador de objetos de Visual Studio, <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2>, pase el <xref:Microsoft.VisualStudio.Shell.Interop.SVsObjectManager> identificador al servicio el `GetService` método.

 Cada biblioteca debe registrar con el Administrador de objetos de Visual Studio, que recopila la información sobre todas las bibliotecas. Para registrar una biblioteca, llame a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterSimpleLibrary%2A> método. Dependiendo de qué herramienta inicia la solicitud, el Administrador de objetos de Visual Studio busca la biblioteca adecuada y solicita los datos. Los datos se transfieren entre las bibliotecas y el [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Administrador de objetos en las listas de símbolos descritos por el <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2> interfaz.

 El [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] es responsable de actualizar periódicamente las herramientas de exploración de símbolos para reflejar los datos más actuales, incluidos en las bibliotecas de administrador de objetos.

 El diagrama siguiente contiene un ejemplo de los elementos clave del proceso de intercambio de solicitudes y los datos entre una biblioteca y el Administrador de objetos de Visual Studio. Las interfaces en el diagrama son parte de una aplicación de código administrado.

 ![Flujo de datos entre una biblioteca y el Administrador de objetos](../../extensibility/internals/media/callbrowserdiagram.gif "CallBrowserDiagram")

 Para proporcionar las listas de símbolos para el Administrador de objetos de Visual Studio, en primer lugar debe registrar la biblioteca con el Administrador de objetos de Visual Studio mediante una llamada a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterSimpleLibrary%2A> método. Una vez que se registra la biblioteca, el Administrador de objetos de Visual Studio solicita cierta información acerca de las capacidades de la biblioteca. Por ejemplo, se solicita a los marcadores de biblioteca y admiten las categorías mediante una llamada a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2.GetLibFlags2%2A> y <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2.GetSupportedCategoryFields2%2A> métodos. En algún momento, cuando una de las herramientas solicita datos de esta biblioteca, el Administrador de objetos solicita la lista de nivel superior de símbolos mediante una llamada a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2.GetList2%2A> método. En respuesta, la biblioteca fabrica una lista de símbolos y los expone en el Administrador de objetos de Visual Studio a través de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2> interfaz. El [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] el Administrador de objetos determina cuántos elementos están en la lista mediante una llamada a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetItemCount%2A> método. Todas las solicitudes siguientes se relacionan con un elemento determinado en la lista y proporcione el número de índice del elemento en cada solicitud. El Administrador de objetos de Visual Studio procede a recopilar la información en el tipo, la accesibilidad y otras propiedades del elemento mediante una llamada a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetCategoryField2%2A> método.

 Determina el nombre del elemento mediante una llamada a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetTextWithOwnership%2A> método y solicita la información de icono mediante una llamada a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetDisplayData%2A> método. El icono se muestra a la izquierda del nombre de elemento y describe el tipo de elemento, la accesibilidad y otras propiedades.

 El [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] objeto manager llama el <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetExpandable3%2A> método para determinar si un elemento de lista determinado es expansible y tiene elementos secundarios. Si la interfaz de usuario envía una solicitud para expandir un elemento, el Administrador de objetos solicita la lista secundaria de símbolos mediante una llamada a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetList2%2A> método. El proceso continúa con las distintas partes del árbol creado a partir de la demanda.

> [!NOTE]
> Para implementar un proveedor de símbolos de código nativo, use el <xref:Microsoft.VisualStudio.Shell.Interop.IVsLibrary2> y <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectList2> interfaces.

## <a name="see-also"></a>Vea también
- [Cómo: Registrar una biblioteca con el Administrador de objetos](../../extensibility/internals/how-to-register-a-library-with-the-object-manager.md)
- [Cómo: Exponer listas de símbolos proporcionadas por la biblioteca al Administrador de objetos](../../extensibility/internals/how-to-expose-lists-of-symbols-provided-by-the-library-to-the-object-manager.md)
- [Cómo: Identificar símbolos en una biblioteca](../../extensibility/internals/how-to-identify-symbols-in-a-library.md)