---
title: Novedades del Control de código fuente en el SDK de Visual Studio 2015 Microsoft Docs
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703406"
---
# <a name="whats-new-in-source-control-for-the-visual-studio-2015-sdk"></a>Novedades del Control de código fuente para el SDK de Visual Studio 2015

En [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]el , puede proporcionar una solución de control de código fuente profundamente integrada mediante la implementación de un control de código fuente VSPackage. En esta sección se describen las características del control de código fuente VSPackages y proporciona información general de los pasos de implementación.

## <a name="the-source-control-vspackage"></a>El control de código fuente VSPackage

Visual Studio admite dos tipos de soluciones de control de código fuente. En todas las versiones de Visual Studio, todavía puede integrar un complemento basado en API de complemento de Control de código fuente. También puede crear un VSPackage para el control [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] de código fuente que proporciona una integración profunda, ruta de acceso adecuada para las soluciones de control de código fuente que requieren un alto nivel de sofisticación y autonomía.

Un VSPackage puede agregar casi cualquier tipo de funcionalidad a Visual Studio. Un control de código fuente VSPackage proporciona una característica de control de código fuente completa para Visual Studio, desde la interfaz de usuario presentada al usuario a la comunicación back-end con el sistema de control de código fuente.

Implementar un control de código fuente VSPackage requiere una estrategia de "todo o nada". El creador de un control de código fuente VSPackage debe invertir una cantidad significativa de esfuerzo en la implementación de una serie de interfaces de control de código fuente y nuevos elementos de interfaz de usuario (cuadros de diálogo, menús y barras de herramientas) para cubrir toda la funcionalidad de control de código fuente, así como las interfaces necesarias de cualquier paquete para integrar se integran correctamente con Visual Studio.

Los pasos siguientes proporcionan una visión general de lo que se necesita para implementar un paquete de control de código fuente. Para obtener más información, vea [Crear un VSPackage](../../extensibility/internals/creating-a-source-control-vspackage.md)de control de código fuente .

1. Cree un VSPackage que ofrezca un servicio de control de código fuente privado.

2. Implemente las interfaces en los servicios relacionados con el control de <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2> código <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider> fuente que ofrece Visual Studio (por ejemplo, la interfaz y la).

3. Registre el control de código fuente VSPackage.

4. Implemente toda la interfaz de usuario del control de código fuente, incluidos los elementos de menú, los cuadros de diálogo, las barras de herramientas y los menús contextuales.

5. Todos los eventos relacionados con el control de código fuente se pasan al control de código fuente VSackage cuando está activo y debe controlarse por el VSPackage.

6. El control de código fuente VSPackage debe <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3> escuchar eventos como los que implementan la interfaz, <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> así como eventos de documento de proyecto de seguimiento (TPD) (según lo implementado por la interfaz) y tomar las medidas necesarias.

## <a name="see-also"></a>Vea también

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>
- [Información general](../../extensibility/internals/source-control-integration-overview.md)
- [Creación de un VSPackage de control de código fuente](../../extensibility/internals/creating-a-source-control-vspackage.md)
