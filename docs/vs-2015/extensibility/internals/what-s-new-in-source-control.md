---
title: Novedades del control de código fuente
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- what's new [Visual Studio SDK], source control
- source control [Visual Studio SDK], what's new
ms.assetid: bcf85418-18fb-4824-9dae-d14bf3d56a77
caps.latest.revision: 28
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 31b55c57f47f25814eff24f13bcf91408468d0f4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68200951"
---
# <a name="what39s-new-in-source-control-in-visual-studio-2015"></a>Novedades de los&#39;en el control de código fuente en Visual Studio 2015

[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

En puede [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] proporcionar una solución de control de código fuente profundamente integrada implementando un VSPackage de control de código fuente. En esta sección se describen las características de los VSPackages de control de código fuente y se proporciona información general sobre los pasos de implementación.  
  
## <a name="the-source-control-vspackage"></a>VSPackage de control de código fuente  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] admite dos tipos de soluciones de control de código fuente. En todas las versiones de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] , todavía puede integrar un complemento basado en la API del complemento de control de código fuente. También puede crear un VSPackage para el control de código fuente, lo que proporciona una ruta de acceso de integración profunda [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] adecuada para las soluciones de control de código fuente que requieren un alto nivel de sofisticación y autonomía.  
  
 Un VSPackage puede Agregar casi cualquier tipo de funcionalidad a [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] . Un VSPackage de control de código fuente proporciona una característica de control de código fuente completa para [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] , desde la interfaz de usuario presentada al usuario hasta la comunicación de back-end con el sistema de control de código fuente.  
  
 La implementación de un VSPackage de control de código fuente requiere una estrategia "todo o nada". El creador de un VSPackage de control de código fuente debe invertir una cantidad significativa de esfuerzo en la implementación de una serie de interfaces de control de código fuente y nuevos elementos de interfaz de usuario (cuadros de diálogo, menús y barras de herramientas) para cubrir toda la funcionalidad de control de código fuente, así como las interfaces necesarias para que cualquier paquete se integre correctamente con [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .  
  
 En los pasos siguientes se proporciona información general sobre lo que se necesita para implementar un paquete de control de código fuente. Para obtener más información, vea [crear un VSPackage de control de código fuente](../../extensibility/internals/creating-a-source-control-vspackage.md).  
  
1. Cree un VSPackage que ofrece un servicio de control de código fuente privado.  
  
2. Implemente las interfaces en los servicios relacionados con el control de código fuente que ofrecidos [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] (por ejemplo, <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2> y la <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider> interfaz).  
  
3. Registre el VSPackage de control de código fuente.  
  
4. Implemente toda la interfaz de usuario del control de código fuente, incluidos los elementos de menú, cuadros de diálogo, barras de herramientas y menús contextuales.  
  
5. Todos los eventos relacionados con el control de código fuente se pasan a su VSackage de control de código fuente cuando está activo y deben ser administrados por el VSPackage.  
  
6. El VSPackage de control de código fuente debe escuchar eventos como los que implementan la <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3> interfaz, así como los eventos de seguimiento de documentos de proyecto (TPD) (tal y como lo implementa la <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> interfaz) y tomar las medidas necesarias.  
  
## <a name="see-also"></a>Consulte también  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>   
 [Visión](../../extensibility/internals/source-control-integration-overview.md)   
 [Creación de un VSPackage de control de código fuente](../../extensibility/internals/creating-a-source-control-vspackage.md)
