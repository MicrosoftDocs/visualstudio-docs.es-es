---
title: "C&#243;mo: identificar s&#237;mbolos en una biblioteca | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Llamar a la herramienta de explorador, identificando los símbolos en la biblioteca"
  - "Herramienta de explorador de llamadas"
ms.assetid: 8fb0de61-71e7-42d1-8b41-2ad915474384
caps.latest.revision: 21
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 21
---
# C&#243;mo: identificar s&#237;mbolos en una biblioteca
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Símbolo\-examinando herramientas muestra las vistas jerárquicas de símbolos.  Los símbolos representan espacios de nombres, objetos, clases, miembros de clase, y otros elementos del lenguaje.  
  
 Cada token de la jerarquía se puede identificar mediante la información de navegación pasa por la biblioteca de símbolos al administrador de objetos de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] a través de las interfaces siguientes:  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfoNode>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumNavInfoNodes>.  
  
 La ubicación del símbolo en la jerarquía distingue un símbolo.  Permite el símbolo\-examinar de herramientas para navegar a un símbolo concreto.  El único, ruta de acceso completa al símbolo determina la ubicación.  Cada elemento de la ruta es un nodo.  La ruta de acceso comienza con el nodo y finaliza de nivel superior con el token específico.  Por ejemplo, si el método M1 es miembro de la clase C1 y C1 está en el espacio de nombres N1, la ruta de acceso completa del método M1 es N1. C1. M1.  esta ruta contiene tres nodos: N1, C1, y M1.  
  
 La información de navegación permite que el administrador de objetos de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] busque, seleccione y conserva seleccionado los símbolos de la jerarquía.  Permite navegar desde una herramienta que vaya a otra.  Mientras que utilizar **Examinador de objetos** para examinar los símbolos en un proyecto, es de [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] hacer clic con el botón secundario en el método y para iniciar la herramienta de **Explorador de llamadas** para mostrar el método en un gráfico de llamadas.  
  
 Dos formularios describen la ubicación del símbolo.  La forma canónica se basa en la ruta de acceso completa del símbolo.  Representa una posición única de símbolos de la jerarquía.  es independiente de la herramienta símbolo\-que examina.  Para obtener información de forma canónica, el administrador de objetos de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] llama a método de <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo.EnumCanonicalNodes%2A> .  El formato de la presentación describe la ubicación del símbolo dentro de una herramienta símbolo\-que examina concreta.  La posición del símbolo es en relación con la posición de otros símbolos en el hierarchicy.  Un símbolo determinado puede tener varias rutas de presentación, pero sólo una ruta canónica.  Por ejemplo, si la clase C1 se hereda de la clase C2 y ambas clases están en el espacio de nombres N1, **Examinador de objetos** muestra el árbol jerárquico siguiente:  
  
```  
N1  
    C1  
        Bases and Interfaces  
            C2  
    C2  
        Bases and Interfaces  
. . . . . . . . . . .  
  
```  
  
 La ruta canónica de la clase C2, en este ejemplo, es N1 \+ C2.  La ruta de C2 incluye nodos C1 y “las bases e interfaces”: N1 \+ C1 \+ “base e interfaces” \+ C2.  
  
 Para obtener información del formato de la presentación, el administrador de objetos llama a método de <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo.EnumPresentationNodes%2A> .  
  
## Identificador de un Símbolo en la jerarquía  
  
#### Para obtener información canónica y de formularios  
  
1.  Implemente el método <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo.EnumCanonicalNodes%2A>.  
  
     El administrador de objetos llama a este método para obtener la lista de nodos contenidos en la ruta canónica de símbolos.  
  
    ```vb#  
    Public Function EnumCanonicalNodes(ByRef ppEnum As Microsoft.VisualStudio.Shell.Interop.IVsEnumNavInfoNodes) As Integer  
        Dim EnumNavInfoNodes As CallBrowserEnumNavInfoNodes = _New CallBrowserEnumNavInfoNodes(m_strMethod)  
        ppEnum = CType(EnumNavInfoNodes, IVsEnumNavInfoNodes)  
        Return 0  
    End Function  
    ```  
  
    ```c#  
    public int EnumCanonicalNodes(out Microsoft.VisualStudio.Shell.Interop.IVsEnumNavInfoNodes ppEnum)  
    {  
        CallBrowserEnumNavInfoNodes EnumNavInfoNodes =  
            new CallBrowserEnumNavInfoNodes(m_strMethod);  
        ppEnum = (IVsEnumNavInfoNodes)(EnumNavInfoNodes);  
        return 0;  
    }  
  
    ```  
  
2.  Implemente el método <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo.EnumPresentationNodes%2A>.  
  
     El administrador de objetos llama a este método para obtener la lista de nodos contenidos en la ruta de la presentación de símbolos.  
  
## Vea también  
 [Compatibilidad con herramientas de exploración de símbolos](../../extensibility/internals/supporting-symbol-browsing-tools.md)   
 [Cómo: registrar una biblioteca con el Administrador de objetos](../../extensibility/internals/how-to-register-a-library-with-the-object-manager.md)   
 [Cómo: exponer listas de símbolos proporcionadas por la biblioteca al administrador de objetos](../../extensibility/internals/how-to-expose-lists-of-symbols-provided-by-the-library-to-the-object-manager.md)