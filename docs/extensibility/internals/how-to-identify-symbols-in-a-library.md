---
title: 'Cómo: Identificar símbolos en una biblioteca ? Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Call Browser tool, identifying symbols in the library
- Call Browser tool
ms.assetid: 8fb0de61-71e7-42d1-8b41-2ad915474384
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1fe920fabd05a875b336467fbba16e4229fa9613
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708002"
---
# <a name="how-to-identify-symbols-in-a-library"></a>Cómo: Identificar símbolos en una biblioteca
Las herramientas de exploración de símbolos muestran vistas jerárquicas de símbolos. Los símbolos representan espacios de nombres, objetos, clases, miembros de clase y otros elementos de lenguaje.

 Cada símbolo de la jerarquía se puede identificar mediante la [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] información de navegación que pasa la biblioteca de símbolos al gestor de objetos a través de las interfaces siguientes:

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfoNode>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumNavInfoNodes>.

 La ubicación del símbolo en la jerarquía distingue un símbolo. Permite que las herramientas de exploración de símbolos naveguen a un símbolo específico. La ruta de acceso única y completa al símbolo determina la ubicación. Cada elemento de la ruta de acceso es un nodo. La ruta de acceso comienza con el nodo de nivel superior y termina con el símbolo específico. Por ejemplo, si el método M1 es miembro de la clase C1 y C1 está en el espacio de nombres N1, la ruta de acceso completa del método M1 es N1. C1. M1. Esta trayectoria contiene tres Nodos: N1, C1 y M1.

 La información de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] navegación permite al administrador de objetos localizar, seleccionar y mantener seleccionados los símbolos de la jerarquía. Permite navegar de una herramienta de navegación a otra. Al utilizar **el Examinador** de [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] objetos para examinar símbolos en un proyecto, puede hacer clic con el botón derecho en un método e iniciar la herramienta Explorador de **llamadas** para mostrar el método en un gráfico de llamadas.

 Dos formularios describen la ubicación del símbolo. La forma canónica se basa en la ruta completa del símbolo. Representa una posición única del símbolo en la jerarquía. Es independiente de la herramienta de exploración de símbolos. Para obtener la información [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] del formulario <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo.EnumCanonicalNodes%2A> canónico, el administrador de objetos llama al método. El formulario de presentación describe la ubicación del símbolo dentro de una herramienta de exploración de símbolos específica. La posición del símbolo es relativa a la posición de otros símbolos en la jerarquía. Un símbolo dado puede tener varias rutas de presentación, pero solo una ruta canónica. Por ejemplo, si la clase C1 se hereda de la clase C2 y ambas clases están en el espacio de nombres N1, el **Examinador de objetos** muestra el siguiente árbol jerárquico:

```
N1
    C1
        Bases and Interfaces
            C2
    C2
        Bases and Interfaces
. . . . . . . . . . .

```

 La ruta canónica de la clase C2, en este ejemplo, es N1 + C2. La ruta de presentación de C2 incluye nodos C1 y "Bases e Interfaces": N1 + C1 + "Bases e Interfaces" + C2.

 Para obtener la información del formulario <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo.EnumPresentationNodes%2A> de presentación, el administrador de objetos llama al método.

## <a name="to-obtain-canonical-and-presentation-forms-information"></a>Para obtener información canónica y de formularios de presentación

1. Implemente el método <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo.EnumCanonicalNodes%2A>.

     El administrador de objetos llama a este método para obtener la lista de nodos contenidos en la ruta canónica del símbolo.

    ```vb
    Public Function EnumCanonicalNodes(ByRef ppEnum As Microsoft.VisualStudio.Shell.Interop.IVsEnumNavInfoNodes) As Integer
        Dim EnumNavInfoNodes As CallBrowserEnumNavInfoNodes = _New CallBrowserEnumNavInfoNodes(m_strMethod)
        ppEnum = CType(EnumNavInfoNodes, IVsEnumNavInfoNodes)
        Return 0
    End Function
    ```

    ```csharp
    public int EnumCanonicalNodes(out Microsoft.VisualStudio.Shell.Interop.IVsEnumNavInfoNodes ppEnum)
    {
        CallBrowserEnumNavInfoNodes EnumNavInfoNodes =
            new CallBrowserEnumNavInfoNodes(m_strMethod);
        ppEnum = (IVsEnumNavInfoNodes)(EnumNavInfoNodes);
        return 0;
    }

    ```

2. Implemente el método <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo.EnumPresentationNodes%2A>.

     El administrador de objetos llama a este método para obtener la lista de nodos contenidos en la ruta de presentación del símbolo.

## <a name="see-also"></a>Vea también
- [Soporta herramientas de navegación de símbolos](../../extensibility/internals/supporting-symbol-browsing-tools.md)
- [Cómo: Registrar una biblioteca con el administrador de objetos](../../extensibility/internals/how-to-register-a-library-with-the-object-manager.md)
- [Cómo: Exponer listas de símbolos proporcionados por la biblioteca al gestor de objetos](../../extensibility/internals/how-to-expose-lists-of-symbols-provided-by-the-library-to-the-object-manager.md)
