---
title: Información general sobre la integración del control de código fuente | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], about source control
ms.assetid: 3a46e4eb-e677-49c3-8647-d927d035a19a
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6f714bfdfc94cb9481071becf1cdc95f5259e975
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2019
ms.locfileid: "72723534"
---
# <a name="source-control-integration-overview"></a>Información general de la integración del control de código fuente
En esta sección se comparan las dos maneras de integrar en el control de código fuente de Visual Studio; Complemento de control de código fuente y VSPackage que proporciona una solución de control de código fuente y resalta las nuevas características de control de código fuente. Visual Studio permite cambiar manualmente entre los paquetes VSPackage de control de código fuente y los complementos de control de código fuente, así como la conmutación automática basada en la solución.

## <a name="source-control-integration"></a>Integración del control de código fuente
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] admite dos tipos de opciones de integración de control de código fuente. En todas las versiones de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], todavía puede integrar un complemento basado en la API del complemento de control de código fuente (anteriormente conocida también como la API MSSCCI), que proporciona la funcionalidad básica de control de código fuente al usar la interfaz de usuario de control de código fuente (UI) de Visual Studio. Un VSPackage de control de código fuente, por otro lado, proporciona una nueva ruta de acceso [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] adecuada para la integración del control de código fuente que requiere un alto nivel de sofisticación y autonomía en su modelo de control de código fuente.

 ![Información general sobre el control de código fuente](../../extensibility/internals/media/sourcectnrloverview.gif "SourceCtnrlOverview")

## <a name="source-control-plug-in"></a>Complemento de control de código fuente
 Todas las versiones de Visual Studio admiten la especificación de la API del complemento de control de código fuente versión 1,2 como ruta de acceso de integración. Un implementador de complemento de control de código fuente escribe un archivo DLL que implementa las funciones de la API del complemento de control de código fuente para la integración y el registro del control de código fuente, tal y como se describe en [crear un complemento de control de código fuente](../../extensibility/internals/creating-a-source-control-plug-in.md). En este enfoque, el entorno de desarrollo integrado (IDE) utiliza la interfaz de usuario de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] para los cuadros de diálogo, como las páginas de propiedades proteger, Desproteger, herramientas/opciones, barras de herramientas y glifos de control de código fuente. El cumplimiento estricto de la API del complemento de control de código fuente garantiza una fácil integración en Visual Studio y una experiencia sin problemas para el usuario. Esto significa que el complemento de control de código fuente debe implementar la mayoría de las funciones y devoluciones de llamada que se detallan en la API.

 Para implementar un complemento de control de código fuente mediante la API del complemento de control de código fuente, siga estos pasos:

1. Cree un archivo DLL que implemente las funciones especificadas en los [Complementos de control de código fuente](../../extensibility/source-control-plug-ins.md).

2. Registre el archivo DLL mediante la realización de las entradas del registro adecuadas (descritas en [Cómo instalar un complemento de control de código fuente](../../extensibility/internals/how-to-install-a-source-control-plug-in.md)).

3. Crear una interfaz de usuario auxiliar y mostrarla cuando se le solicite el paquete del adaptador de control de código fuente (el componente de Visual Studio que controla la funcionalidad de control de código fuente a través de complementos de control de código fuente)

   En respuesta a un comando de control de código fuente, el IDE de Visual Studio presenta una interfaz de usuario estándar para las operaciones básicas y, a continuación, pasa la información al complemento de control de código fuente a través de las funciones definidas en la API del complemento de control de código fuente. Para las opciones avanzadas, se puede llamar al complemento de control de código fuente en para presentar su propia interfaz de usuario, por ejemplo, buscar un proyecto controlado por código fuente. Esto significa que el usuario puede presentar dos estilos posiblemente diferentes de la interfaz de usuario al tratar el control de código fuente: la interfaz de usuario que Visual Studio presenta y la interfaz de usuario que presenta el complemento de control de código fuente. Esto es más evidente con las operaciones avanzadas de control de código fuente.

### <a name="drawbacks-to-implementing-a-source-control-plug-in"></a>Desventajas de la implementación de un complemento de control de código fuente

- En el caso de las características avanzadas, el usuario puede ver dos estilos diferentes de interfaces, lo que conduce a una posible confusión.

- El complemento de control de código fuente se limita al modelo de control de código fuente implicado por la API del complemento de control de código fuente.

- La API del complemento de control de código fuente puede ser demasiado restrictiva en algunos escenarios de control de código fuente.

### <a name="advantages-to-implementing-a-source-control-plug-in"></a>Ventajas de implementar un complemento de control de código fuente

- Visual Studio proporciona toda la interfaz de usuario para todas las operaciones básicas de control de código fuente para que el complemento de control de código fuente no tenga que implementar la interfaz de usuario potencialmente compleja.

- Debido a la API estricta, el complemento de control de código fuente puede interactuar fácilmente con los programas de control de código fuente externos para proporcionar una funcionalidad más amplia. Visual Studio no es más importante cómo se realiza la funcionalidad de control de código fuente, solo que se realiza según la API del complemento de control de código fuente.

- Es más fácil implementar un complemento de control de código fuente que un VSPackage de control de código fuente.

## <a name="source-control-vspackage"></a>VSPackage de control de código fuente
 [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] permite la integración profunda en Visual Studio con control total de la funcionalidad de control de código fuente y el reemplazo completo de la interfaz de usuario del control de código fuente proporcionado por Visual Studio. Un VSPackage de control de código fuente se registra con Visual Studio y proporciona la funcionalidad de control de código fuente. Aunque se pueden registrar varios VSPackages de control de código fuente con Visual Studio, solo uno de ellos puede estar activo en cualquier momento. Un VSPackage de control de código fuente tiene control total sobre la funcionalidad de control de código fuente y la apariencia en Visual Studio mientras está activo. Todos los demás VSPackages de control de código fuente que se pueden registrar en el sistema están inactivos y no mostrarán ninguna interfaz de usuario.

 La implementación de un VSPackage de control de código fuente requiere una estrategia "todo o nada". El creador de un VSPackage de control de código fuente debe invertir una cantidad significativa de esfuerzo en la implementación de una serie de interfaces de control de código fuente y nuevos elementos de interfaz de usuario (cuadros de diálogo, menús y barras de herramientas) para cubrir toda la funcionalidad de control de código fuente. Vea [crear un VSPackage de control de código fuente](../../extensibility/internals/creating-a-source-control-vspackage.md) para obtener más detalles.

### <a name="drawbacks-to-implementing-a-source-control-vspackage"></a>Desventajas de implementar un VSPackage de control de código fuente

- El VSPackage debe implementar una serie de interfaces complejas para integrarse correctamente con Visual Studio.

- El VSPackage debe proporcionar toda la interfaz de usuario necesaria para el control de código fuente; Visual Studio no proporcionará asistencia en esta área.

- Un VSPackage de control de código fuente está vinculado íntimamente a Visual Studio y no puede funcionar con programas independientes, por lo que la funcionalidad no se puede compartir fácilmente con una versión externa del programa de control de código fuente.

### <a name="advantages-to-implementing-a-source-control-vspackage"></a>Ventajas de implementar un VSPackage de control de código fuente

- Dado que el VSPackage tiene control total sobre la interfaz de usuario y la funcionalidad de control de código fuente, se presenta una interfaz perfecta para el control de código fuente.

- El VSPackage no se limita a un modelo de control de código fuente determinado.

## <a name="see-also"></a>Vea también
- [Control de código fuente](../../extensibility/internals/source-control.md)
- [Creación de un complemento de control de código fuente](../../extensibility/internals/creating-a-source-control-plug-in.md)
- [Creación de un VSPackage de control de código fuente](../../extensibility/internals/creating-a-source-control-vspackage.md)
- [Novedades del control de código fuente](../../extensibility/internals/what-s-new-in-source-control.md)