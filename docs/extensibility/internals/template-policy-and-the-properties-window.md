---
title: Directiva de plantilla y la ventana Propiedades ( Template Policy) y Properties (Propiedades) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Properties window, template policy
ms.assetid: 1d8019d3-5e57-47ba-b358-526b0796a63b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 08ed6f416441d06767661e63b5e32454dbe07f93
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704661"
---
# <a name="template-policy-and-the-properties-window"></a>Directiva de plantilla y ventana Propiedades
Cuando un proyecto está contenido dentro de un proyecto de plantilla de empresa, ese proyecto de plantilla de empresa puede aplicar la directiva. La directiva de plantilla se convierte en un sistema de restricción que se puede usar para establecer valores predeterminados para propiedades, ocultar propiedades, agregar propiedades, etc.

 El uso de la directiva de **Properties** plantilla para controlar <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>la visualización de información en la ventana Propiedades es diferente de la implementación de . <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>controla las propiedades de los objetos en el nivel de componente, mientras que la directiva de plantilla se puede utilizar para restringir las propiedades de objeto en el nivel de solución o proyecto. En otras palabras,

- Implemente los <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing> métodos para determinar lo que se muestra en la ventana **Propiedades** para objetos específicos

- Use la directiva de plantilla en el nivel de solución y proyecto para determinar lo que se muestra en la ventana **Propiedades** para los objetos especificados anteriormente

  El uso de la directiva de plantilla para restringir selectivamente propiedades específicas en la ventana **Propiedades** cuando se selecciona un elemento de proyecto de un tipo especificado en el **Explorador** de soluciones puede ser beneficioso para todos los miembros del equipo de desarrollo que trabajan en un proyecto. Por ejemplo, mediante la directiva de plantilla, puede configurar toda la información de cadena de conexión en una base de datos para los desarrolladores y hacer que la cadena de conexión sea de solo lectura. De este modo, puede proporcionar una forma sencilla de asegurarse de que cada desarrollador utiliza la ruta de acceso correcta para el acceso a los datos.

## <a name="see-also"></a>Vea también
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>
- [Extensión de propiedades](../../extensibility/internals/extending-properties.md)
