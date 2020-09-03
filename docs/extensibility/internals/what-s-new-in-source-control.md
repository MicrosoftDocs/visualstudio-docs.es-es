---
title: Novedades del control de código fuente en el SDK de 2015 de Visual Studio | Microsoft Docs
titleSuffix: ''
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- what's new [Visual Studio SDK], source control
- source control [Visual Studio SDK], what's new
ms.assetid: bcf85418-18fb-4824-9dae-d14bf3d56a77
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f90ae3e1d327b10e99713ad28aa2d5a06c0be34b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "80703406"
---
# <a name="whats-new-in-source-control-for-the-visual-studio-2015-sdk"></a>Novedades del control de código fuente para el SDK de Visual Studio 2015

En [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] , puede proporcionar una solución de control de código fuente profundamente integrada implementando un VSPackage de control de código fuente. En esta sección se describen las características de los VSPackages de control de código fuente y se proporciona información general sobre los pasos de implementación.

## <a name="the-source-control-vspackage"></a>VSPackage de control de código fuente

Visual Studio admite dos tipos de soluciones de control de código fuente. En todas las versiones de Visual Studio, todavía puede integrar un complemento basado en la API del complemento de control de código fuente. También puede crear un VSPackage para el control de código fuente que proporciona una ruta de acceso de integración profunda [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] adecuada para las soluciones de control de código fuente que requieren un alto nivel de sofisticación y autonomía.

Un VSPackage puede Agregar casi cualquier tipo de funcionalidad a Visual Studio. Un VSPackage de control de código fuente proporciona una característica de control de código fuente completa para Visual Studio, desde la interfaz de usuario presentada al usuario hasta la comunicación de back-end con el sistema de control de código fuente.

La implementación de un VSPackage de control de código fuente requiere una estrategia "todo o nada". El creador de un VSPackage de control de código fuente debe invertir una cantidad significativa de esfuerzo en la implementación de una serie de interfaces de control de código fuente y nuevos elementos de interfaz de usuario (cuadros de diálogo, menús y barras de herramientas) para cubrir toda la funcionalidad de control de código fuente, así como las interfaces necesarias de cualquier paquete para integrarse correctamente con Visual Studio.

En los pasos siguientes se proporciona información general sobre lo que se necesita para implementar un paquete de control de código fuente. Para obtener más información, vea [crear un VSPackage de control de código fuente](../../extensibility/internals/creating-a-source-control-vspackage.md).

1. Cree un VSPackage que ofrece un servicio de control de código fuente privado.

2. Implemente las interfaces en los servicios relacionados con el control de código fuente que ofrecidos Visual Studio (por ejemplo, la <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2> <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider> interfaz y).

3. Registre el VSPackage de control de código fuente.

4. Implemente toda la interfaz de usuario del control de código fuente, incluidos los elementos de menú, cuadros de diálogo, barras de herramientas y menús contextuales.

5. Todos los eventos relacionados con el control de código fuente se pasan a su VSackage de control de código fuente cuando está activo y deben ser administrados por el VSPackage.

6. El VSPackage de control de código fuente debe escuchar eventos como los que implementan la <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3> interfaz, así como los eventos de seguimiento de documentos de proyecto (TPD) (tal y como lo implementa la <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> interfaz) y tomar las medidas necesarias.

## <a name="see-also"></a>Vea también

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>
- [Información general](../../extensibility/internals/source-control-integration-overview.md)
- [Creación de un VSPackage de control de código fuente](../../extensibility/internals/creating-a-source-control-vspackage.md)
