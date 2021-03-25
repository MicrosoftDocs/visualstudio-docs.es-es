---
title: Directiva de plantilla y la ventana Propiedades | Microsoft Docs
description: Obtenga información sobre el uso de la Directiva de plantilla para establecer los valores predeterminados para las propiedades, ocultar propiedades y agregar propiedades en el ventana Propiedades.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Properties window, template policy
ms.assetid: 1d8019d3-5e57-47ba-b358-526b0796a63b
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: b415054f65c41f03556f7d87be5b12d92ced399c
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105078674"
---
# <a name="template-policy-and-the-properties-window"></a>Directiva de plantilla y ventana Propiedades
Cuando un proyecto se encuentra dentro de un proyecto de Enterprise Templates, ese proyecto de plantilla de empresa puede aplicar la Directiva. La Directiva de plantilla se convierte en un sistema de restricción que se puede usar para establecer los valores predeterminados de las propiedades, ocultar propiedades, agregar propiedades, etc.

 El uso de la Directiva de plantilla para controlar la visualización de la información en la ventana **propiedades** es diferente de la implementación de <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing> . <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing> controla las propiedades de objeto en el nivel de componente, mientras que la Directiva de plantilla se puede usar para restringir las propiedades de objeto en el nivel de solución o proyecto. En otras palabras

- Implemente los métodos en <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing> para determinar lo que se muestra en la ventana **propiedades** para objetos específicos.

- Use la Directiva de plantilla en el nivel de solución y de proyecto para determinar lo que se muestra en la ventana **propiedades** para los objetos previamente especificados.

  Usar la Directiva de plantilla para restringir de forma selectiva propiedades específicas en la ventana **propiedades** cuando se selecciona un elemento de proyecto de un tipo especificado en **Explorador de soluciones** puede ser beneficioso para todos los miembros del equipo de desarrollo que trabajan en un proyecto. Por ejemplo, mediante la Directiva de plantilla, puede configurar toda la información de la cadena de conexión en una base de datos para los desarrolladores y hacer que la cadena de conexión sea de solo lectura. De este modo, puede proporcionar una manera sencilla de garantizar que cada desarrollador use la ruta de acceso correcta para el acceso a los datos.

## <a name="see-also"></a>Consulte también
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>
- [Extensión de propiedades](../../extensibility/internals/extending-properties.md)
