---
title: "Novedades de Control de c&#243;digo fuente | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "¿Qué es el nuevo control de código fuente [Visual Studio SDK],"
  - "control de código fuente [Visual Studio SDK], novedades"
ms.assetid: bcf85418-18fb-4824-9dae-d14bf3d56a77
caps.latest.revision: 27
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 27
---
# Novedades de Control de c&#243;digo fuente
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

En [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] puede proporcionar una solución de control de código fuente de profundidad integrada implementando un control de código fuente VSPackage.  Esta sección describe las características de control de código fuente VSPackages y proporciona información general de los pasos de implementación.  
  
## El control de código fuente VSPackage  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] admite dos tipos de soluciones de control de código fuente.  En todas las versiones de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], todavía puede integrar un complemento API\-basado complemento de control de código fuente.  También puede crear un Paquete para el control de código fuente que proporciona una profundo\-integración, ruta de [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] adecuado para las soluciones de control de código fuente que requieren un alto nivel de la sofisticación y la autonomía.  
  
 Un Paquete puede agregar casi cualquier tipo de funcionalidad a [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  Un control de origen VSPackage proporciona una característica completa de control de código fuente para [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], la interfaz de usuario ante el usuario a la comunicación back\-end con el sistema de control de código fuente.  
  
 implementar un control de código fuente VSPackage no requiere un “todo o nada” estrategia.  El creador de un control de origen VSPackage debe invertir un esfuerzo significativo en implementar varias interfaces de control de código fuente y nuevos elementos de la interfaz de usuario \(cuadros de diálogo, menús, y barras de herramientas\) para cubrir toda la funcionalidad del control de código fuente, así como las interfaces necesarias de cualquier paquete para integrar correctamente con [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
 Los pasos siguientes proporcionan información general sobre lo que es necesario implementar un paquete de control de código fuente.  Para obtener información detallada, vea [Crear un VSPackage del Control de código fuente](../../extensibility/internals/creating-a-source-control-vspackage.md).  
  
1.  Cree un Paquete que genere un servicio de control de código fuente privado.  
  
2.  Implementar las interfaces de los servicios CONTROL\-relacionados de origen que son ofrecidos por [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] \(por ejemplo, <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2> y la interfaz de <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider> \).  
  
3.  registre el control de código fuente VSPackage.  
  
4.  Implementar toda la interfaz de usuario del control de código fuente, como los elementos de menú, cuadros de diálogo, barras de herramientas, y menús contextuales.  
  
5.  Todos los eventos CONTROL\-relacionados de origen se pasan al control de código fuente VSackage cuando está activo y debe ser administrado por el paquete VSPackage.  
  
6.  El control de código fuente VSPackage debe escuchar los eventos como los que implementan la interfaz de <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3> así como eventos de documento de \(TPD\) proyecto de pista \(implementados por la interfaz de <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> \) y realizar acciones necesarias.  
  
## Vea también  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>   
 [Información general](../../extensibility/internals/source-control-integration-overview.md)   
 [Crear un VSPackage del Control de código fuente](../../extensibility/internals/creating-a-source-control-vspackage.md)