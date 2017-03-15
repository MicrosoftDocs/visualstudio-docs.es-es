---
title: "Implementaci&#243;n de paquetes VSPackage mediante Visual Studio Library | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Visual Studio Library, implementar paquetes VSPackage"
ms.assetid: 4cbac13f-2a9d-4955-b411-dad79081fdeb
caps.latest.revision: 7
caps.handback.revision: 7
manager: "douge"
---
# Implementaci&#243;n de paquetes VSPackage mediante Visual Studio Library
la clase de `IVsPackageImpl` en la biblioteca de Visual Studio proporciona una implementación mínima de la interfaz de <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage> .  `IVsPackageImpl` toma cuidado la mayoría de los métodos de mantenimiento de <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>.  Otros métodos que necesite para reemplazar para proporcionar una incluyen significativa de implementación:  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A>  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.CreateTool%2A>  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.ResetDefaults%2A>  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A>  
  
    > [!NOTE]
    >  La plantilla de paquete de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] genera todo el código que aquí.  Puede guardar hora mediante la plantilla de generar un VSPackage automáticamente.  
  
 Los paquetes que se implementan mediante la biblioteca de Visual Studio normalmente heredar una clase de Paquete de [CComObjectRootEx Class](/visual-cpp/atl/reference/ccomobjectrootex-class) ATL y de [CComCoClass Class](/visual-cpp/atl/reference/ccomcoclass-class) y de IVsPackageImpl de la biblioteca de Visual Studio.  Por ejemplo, lo siguiente es la declaración de clase de Paquete de ejemplo de Reference.Package:  
  
```  
class ATL_NO_VTABLE BasicPackage :   
    public CComObjectRootEx<CComSingleThreadModel>,  
    public CComCoClass<BasicPackage, &CLSID_BasicPackage>,  
    public IVsPackageImpl<BasicPackage, &CLSID_BasicPackage>,  
    ...  
```  
  
 Los parámetros de plantilla de `IVsPackageImpl` mostrados son la propia clase de VSPackage y puntero a un GUID que identifica el paquete VSPackage.  
  
## Admitir QueryInterface con mapas COM  
 Para obtener compatibilidad con ATL para `QueryInterface`, el mapa COM debe mostrar las interfaces que la clase implementa.  Por ejemplo, lo siguiente es el mapa COM para la clase de Paquete en el ejemplo de Reference.Package:  
  
```  
BEGIN_COM_MAP(BasicPackage)  
    COM_INTERFACE_ENTRY(IVsPackage)  
    ...  
END_COM_MAP()  
```  
  
 Para obtener más información sobre asignación COM, vea [Implementing CComObjectRootEx](/visual-cpp/atl/implementing-ccomobjectrootex) y [COM\_INTERFACE\_ENTRY Macros](../Topic/COM_INTERFACE_ENTRY%20Macros.md).  
  
## Admitir el registro con los mapas del registro  
 La biblioteca de Visual Studio utiliza archivos de ATL\-estilo .RGS para admitir el registro de objetos COM.  Para admitir el reemplazo del token en el archivo de .RGS, la biblioteca de Visual Studio utiliza asignaciones de registro.  Los mapas del registro muestran los símbolos que se reemplazarán y admiten el uso de los id. para los recursos de la tabla de cadenas.  
  
 Por ejemplo, lo siguiente es el registro asignado para la clase de Paquete en el ejemplo de Reference.Package:  
  
```  
VSL_BEGIN_REGISTRY_MAP(IDR_BASICPACKAGE_RGS)  
    VSL_REGISTRY_MAP_GUID_ENTRY(CLSID_BasicPackage)  
    VSL_REGISTRY_RESOURCE_STRING_ENTRY(IDS_BASICPACKAGE_REGISTRY_NAME)  
    ...  
VSL_END_REGISTRY_MAP()  
```  
  
## Vea también  
 [Muestras de VSSDK](../misc/vssdk-samples.md)