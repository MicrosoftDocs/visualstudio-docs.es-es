---
title: 'Cómo: identificar los símbolos en una biblioteca | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Call Browser tool, identifying symbols in the library
- Call Browser tool
ms.assetid: 8fb0de61-71e7-42d1-8b41-2ad915474384
caps.latest.revision: 22
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 2f10cc65d30f8d9b2d58fa02822494ae7e6a6940
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47581067"
---
# <a name="how-to-identify-symbols-in-a-library"></a>Cómo: identificar los símbolos en una biblioteca
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [Cómo: identificar los símbolos en una biblioteca](https://docs.microsoft.com/visualstudio/extensibility/internals/how-to-identify-symbols-in-a-library).  
  
Herramientas de exploración de símbolos muestran las vistas jerárquicas de símbolos. Los símbolos representan espacios de nombres, objetos, clases, miembros de clase y otros elementos de lenguaje.  
  
 Cada símbolo en la jerarquía puede identificarse por la información de navegación pasada por la biblioteca de símbolos para el [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] el Administrador de objetos a través de las interfaces siguientes:  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfoNode>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumNavInfoNodes>.  
  
 La ubicación del símbolo de la jerarquía distingue un símbolo. Permite que las herramientas de exploración de símbolos Navegar a un símbolo concreto. La ruta de acceso completamente calificado al símbolo determina la ubicación. Cada elemento de la ruta de acceso es un nodo. La ruta de acceso comienza con el nodo de nivel superior y finaliza con el símbolo específico. Por ejemplo, si el método M1 es un miembro de la clase C1 y C1 se encuentra en el espacio de nombres N1, la ruta de acceso completa del método M1 es N1. C1. M1. Esta ruta de acceso contiene tres nodos: N1, C1 y M1.  
  
 La información de navegación permite la [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Administrador de objetos para buscar, seleccione y mantenga seleccionado los símbolos en la jerarquía. Permite navegar desde una herramienta de exploración a otro. Al usar **Examinador de objetos** para buscar símbolos en un [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] proyecto, puede a la derecha, haga clic en un método e iniciar el **Examinador de llamadas** herramienta que muestra el método en un gráfico de llamadas.  
  
 Dos formas describen la posición del símbolo. El formato canónico se basa en la ruta de acceso completa del símbolo. Representa una posición única del símbolo en la jerarquía. Es independiente de la herramienta de exploración de símbolos. Para obtener la información de la forma canónica, el [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] de objeto llama manager <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo.EnumCanonicalNodes%2A> método. El formulario de presentación describe la ubicación del símbolo en una herramienta de exploración de símbolos específico. La posición del símbolo es relativo a la posición de otros símbolos en el hierarchicy. Un símbolo determinado puede tener varias rutas de acceso de la presentación, pero solo una ruta de acceso canónica. Por ejemplo, si la clase C1 se hereda de la clase C2 y ambas clases se encuentran en el espacio de nombres N1, el **Examinador de objetos** muestra el árbol de jerarquía siguiente:  
  
```  
N1  
    C1  
        Bases and Interfaces  
            C2  
    C2  
        Bases and Interfaces  
. . . . . . . . . . .  
  
```  
  
 La ruta de acceso canónica de la clase C2, en este ejemplo, es N1 + C2. La ruta de acceso de presentación de C2 incluye nodos C1 y "Bases y las Interfaces": N1 + C1 + "Bases y las Interfaces" + C2.  
  
 Para obtener la información del formulario de presentación, el Administrador de objetos llama <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo.EnumPresentationNodes%2A> método.  
  
## <a name="identifying-a-symbol-in-the-hierarchy"></a>Identificar un símbolo en la jerarquía  
  
#### <a name="to-obtain-canonical-and-presentation-forms-information"></a>Para obtener canónico y presentación de información de formularios  
  
1.  Implemente el método <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo.EnumCanonicalNodes%2A>.  
  
     El Administrador de objetos llama a este método para obtener la lista de nodos contenidos en la ruta de acceso canónica del símbolo.  
  
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
  
2.  Implemente el método <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo.EnumPresentationNodes%2A>.  
  
     El Administrador de objetos llama a este método para obtener la lista de nodos contenidos en la ruta de acceso de presentación del símbolo.  
  
## <a name="see-also"></a>Vea también  
 [Herramientas de exploración de símbolos de compatibilidad](../../extensibility/internals/supporting-symbol-browsing-tools.md)   
 [Cómo: registrar una biblioteca con el Administrador de objetos](../../extensibility/internals/how-to-register-a-library-with-the-object-manager.md)   
 [Exposición de listas de símbolos proporcionadas por la biblioteca al Administrador de objetos](../../extensibility/internals/how-to-expose-lists-of-symbols-provided-by-the-library-to-the-object-manager.md)

