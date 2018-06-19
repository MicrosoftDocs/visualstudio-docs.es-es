---
title: ¿Qué&#39;s de Control de código fuente | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- what's new [Visual Studio SDK], source control
- source control [Visual Studio SDK], what's new
ms.assetid: bcf85418-18fb-4824-9dae-d14bf3d56a77
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b46730ab1acac6605af2e1ff1c418dbe8c886406
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
ms.locfileid: "31137773"
---
# <a name="what39s-new-in-source-control"></a>¿Qué&#39;s de Control de código fuente
En [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] puede proporcionar una solución de control de código fuente profundamente integrado mediante la implementación de un control de código fuente VSPackage. En esta sección se describe las características de control de código fuente VSPackages y proporciona una visión general de los pasos de implementación.  
  
## <a name="the-source-control-vspackage"></a>El VSPackage del Control de código fuente  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] admite dos tipos de soluciones de control de código fuente. En todas las versiones de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], aún podrá integrar basado en la API de complementos de Control de origen de complemento. También puede crear un VSPackage para control de código fuente que proporciona una integración profunda, [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] ruta de acceso adecuado para las soluciones de control de código fuente que requieren un alto nivel de sofisticación y autonomía.  
  
 Un VSPackage puede agregar casi cualquier tipo de funcionalidad a [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Un control de código fuente VSPackage proporciona una característica de control de código fuente completo para [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], desde la UI presentada al usuario para la comunicación de back-end con el sistema de control de código fuente.  
  
 La implementación de un control de código fuente VSPackage requiere una estrategia de "todo o nada". El creador de un control de código fuente VSPackage debe invertir una cantidad considerable de esfuerzo en la implementación de una serie de interfaces de control de código fuente y los nuevos elementos de interfaz de usuario (cuadros de diálogo, menús y barras de herramientas) para cubrir la funcionalidad de control de código fuente, así como interfaces requiere de un paquete para integrarse correctamente con [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
 Los pasos siguientes ofrecen una visión general de lo que es necesario para implementar un paquete de control de código fuente. Para obtener más información, consulte [crear un VSPackage de Control de código fuente](../../extensibility/internals/creating-a-source-control-vspackage.md).  
  
1.  Crear un VSPackage que proffers un servicio de control de código fuente privada.  
  
2.  Implementar las interfaces en los servicios relacionados con el control de código fuente ofrecidos por [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] (por ejemplo, el <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2> y <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider> interfaz).  
  
3.  Registre el VSPackage del control de código fuente.  
  
4.  Implementar todo el control de origen interfaz de usuario, incluidos los elementos de menú, cuadros de diálogo, barras de herramientas y menús contextuales.  
  
5.  Todos los eventos relacionados con el control de origen se pasan al control de código fuente VSackage cuando está activo y serán administrada por el VSPackage.  
  
6.  Control de código fuente VSPackage debe escuchar eventos tales como implementación el <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3> , así como eventos de documento de proyecto de seguimiento (TPD) de la interfaz (tal como lo implementan las <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> interfaz) y tomar las medidas necesarias.  
  
## <a name="see-also"></a>Vea también  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>   
 [Información general](../../extensibility/internals/source-control-integration-overview.md)   
 [Creación de un VSPackage de control de código fuente](../../extensibility/internals/creating-a-source-control-vspackage.md)