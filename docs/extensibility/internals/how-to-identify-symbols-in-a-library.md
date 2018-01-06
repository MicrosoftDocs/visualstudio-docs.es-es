---
title: "Cómo: identificar símbolos en una biblioteca | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Call Browser tool, identifying symbols in the library
- Call Browser tool
ms.assetid: 8fb0de61-71e7-42d1-8b41-2ad915474384
caps.latest.revision: "21"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 60365f3722ae4e2c1f8b52dacc3df03840fb3304
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-identify-symbols-in-a-library"></a>Cómo: identificar símbolos en una biblioteca
Herramientas de exploración de símbolo de mostrar una vista jerárquica de los símbolos. Los símbolos representan espacios de nombres, objetos, clases, miembros de clase y otros elementos del lenguaje.  
  
 Cada símbolo en la jerarquía puede identificarse mediante la información de navegación que se pasa por la biblioteca de símbolos para el [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] el Administrador de objetos a través de las interfaces siguientes:  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfoNode>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumNavInfoNodes>.  
  
 La ubicación del símbolo de la jerarquía distingue un símbolo. Permite que las herramientas de exploración de símbolos Navegar a un símbolo concreto. La ruta de acceso completamente calificado al símbolo determina la ubicación. Cada elemento de la ruta de acceso es un nodo. La ruta de acceso comienza con el nodo de nivel superior y finaliza con el símbolo específico. Por ejemplo, si el método M1 es un miembro de la clase C1 y C1 se encuentra en el espacio de nombres N1, la ruta de acceso completa del método M1 es N1. C1. M1. Esta ruta de acceso contiene tres nodos: N1, C1 y M1.  
  
 La información de exploración permite el [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] el Administrador de objetos para buscar, seleccione y mantenga seleccionado los símbolos en la jerarquía. Permite navegar desde una herramienta de exploración a otra. Al usar **Examinador de objetos** para buscar símbolos en una [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] proyecto, puede haga clic en un método e iniciar la **Examinador de llamadas** herramienta que muestra el método en un gráfico de llamadas.  
  
 La posición del símbolo describen los dos formatos. El formato canónico se basa en la ruta de acceso completa del símbolo. Representa una única posición del símbolo en la jerarquía. Es independiente de la herramienta de exploración de símbolos. Para obtener la información de la forma canónica, el [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] objeto administrador llamadas <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo.EnumCanonicalNodes%2A> método. El formato de presentación describe la ubicación del símbolo dentro de una herramienta de exploración de símbolo específico. La posición del símbolo es relativo a la posición de otros símbolos en el hierarchicy. Un símbolo determinado puede tener varias rutas de acceso de la presentación, pero solo una ruta de acceso canónica. Por ejemplo, si C1 clase se hereda de la clase C2 y ambas clases se encuentran en el espacio de nombres N1, la **Examinador de objetos** muestra el árbol de jerarquía siguiente:  
  
```  
N1  
    C1  
        Bases and Interfaces  
            C2  
    C2  
        Bases and Interfaces  
. . . . . . . . . . .  
  
```  
  
 La ruta de acceso canónica de la clase C2, en este ejemplo, es N1 + C2. La ruta de acceso de presentación de C2 incluye nodos C1 y "Bases y Interfaces": N1 + C1 + "Bases y Interfaces" + C2.  
  
 Para obtener la información de formato de presentación, las llamadas de administrador de objeto <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo.EnumPresentationNodes%2A> método.  
  
## <a name="identifying-a-symbol-in-the-hierarchy"></a>Identificación de un símbolo en la jerarquía  
  
#### <a name="to-obtain-canonical-and-presentation-forms-information"></a>Para obtener canónico y presentación de información de formularios  
  
1.  Implemente el método <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo.EnumCanonicalNodes%2A>.  
  
     El Administrador de objetos llama a este método para obtener la lista de nodos incluidos en la ruta de acceso canónica del símbolo.  
  
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
  
     El Administrador de objetos llama a este método para obtener la lista de nodos incluidos en la ruta de acceso de presentación del símbolo.  
  
## <a name="see-also"></a>Vea también  
 [Compatibilidad con herramientas de exploración de símbolos](../../extensibility/internals/supporting-symbol-browsing-tools.md)   
 [Cómo: registrar una biblioteca con el Administrador de objetos](../../extensibility/internals/how-to-register-a-library-with-the-object-manager.md)   
 [Exposición de listas de símbolos proporcionadas por la biblioteca al Administrador de objetos](../../extensibility/internals/how-to-expose-lists-of-symbols-provided-by-the-library-to-the-object-manager.md)