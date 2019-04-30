---
title: Novedades en Control de código fuente en el SDK Visual Studio 2015 | Microsoft Docs
titleSuffix: ''
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- what's new [Visual Studio SDK], source control
- source control [Visual Studio SDK], what's new
ms.assetid: bcf85418-18fb-4824-9dae-d14bf3d56a77
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3b667a6c6322a925b49290ab3234788a4eee3544
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62856790"
---
# <a name="whats-new-in-source-control-for-the-visual-studio-2015-sdk"></a>Novedades en Control de código fuente para el SDK Visual Studio 2015

En el [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)], puede proporcionar una solución de control de código fuente está profundamente integrado mediante la implementación de un VSPackage de control de código fuente. En esta sección se describe las características de control de código fuente VSPackages y proporciona información general sobre los pasos de implementación.

## <a name="the-source-control-vspackage"></a>El VSPackage de Control de código fuente

Visual Studio admite dos tipos de soluciones de control de código fuente. En todas las versiones de Visual Studio, aún podrá integrar basada en API de complemento de Control de origen de complemento. También puede crear un VSPackage de control de código fuente que proporciona una integración profunda, [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] ruta de acceso adecuado para soluciones de control de código fuente que requieren un alto nivel de sofisticación y la autonomía.

Un VSPackage puede agregar casi cualquier tipo de funcionalidad a Visual Studio. Un VSPackage de control de código fuente proporciona una característica de control de código fuente completo para Visual Studio, desde la UI presentada al usuario para la comunicación de back-end con el sistema de control de código fuente.

Implementación de un VSPackage de control de código fuente, requiere una estrategia de "todo o nada". El creador de un VSPackage de control de código fuente debe invertir una cantidad considerable de esfuerzo en la implementación de una serie de interfaces del control de código fuente y los nuevos elementos de interfaz de usuario (cuadros de diálogo, menús y barras de herramientas) para cubrir la funcionalidad de control de código fuente completo, así como interfaces requiere de un paquete para una integración correcta con Visual Studio.

Los pasos siguientes dan una visión general de lo que es necesario para implementar un paquete de control de código fuente. Para obtener más información, consulte [crear un VSPackage de Control de código fuente](../../extensibility/internals/creating-a-source-control-vspackage.md).

1. Cree un VSPackage que ofrece un servicio de control de origen privado.

2. Implementar las interfaces en los servicios relacionados con el control de código fuente son ofrecidos por Visual Studio (por ejemplo, el <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2> y <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider> interfaz).

3. Registre el VSPackage de control de código fuente.

4. Implementar el control de código fuente todas la interfaz de usuario, incluidos los elementos de menú, cuadros de diálogo, barras de herramientas y menús contextuales.

5. Todos los eventos relacionados con el control de origen se pasan al control de código fuente VSackage cuando está activo y debe controlarse mediante el paquete de VS.

6. El VSPackage de control de código fuente debe escuchar eventos tales como implementación el <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3> , así como los eventos de documento de proyecto de pista (TPD) de la interfaz (tal como está implementado por el <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> interfaz) y tomar las medidas necesarias.

## <a name="see-also"></a>Vea también

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>
- [Información general](../../extensibility/internals/source-control-integration-overview.md)
- [Creación de un VSPackage de control de código fuente](../../extensibility/internals/creating-a-source-control-vspackage.md)