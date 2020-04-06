---
title: Descripción general de la integración de Control de código fuente (Source Control Integration Overview Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], about source control
ms.assetid: 3a46e4eb-e677-49c3-8647-d927d035a19a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d80363286f5f0cac9a5ceb2e8ac9d20345df9e6f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705123"
---
# <a name="source-control-integration-overview"></a>Información general de la integración del control de código fuente
En esta sección se comparan las dos formas de integrar seingen en el control de código fuente de Visual Studio; un complemento de control de código fuente y un VSPackage que proporciona una solución de control de código fuente y resalta las nuevas características de control de código fuente. Visual Studio permite la conmutación manual entre VSPackages de control de código fuente y complementos de control de código fuente, así como conmutación automática basada en solución.

## <a name="source-control-integration"></a>Integración del control de código fuente
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]admite dos tipos de opciones de integración de control de código fuente. En todas [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]las versiones de , todavía puede integrar un complemento basado en la API de complemento de Control de código fuente (anteriormente también conocida como la API de MSSCCI), que proporciona funcionalidad básica de control de código fuente mientras usa la interfaz de usuario (UI) del control de código fuente de Visual Studio. Un control de código fuente VSPackage, por otro [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] lado, proporciona una nueva ruta de acceso de integración profunda adecuada para la integración de control de código fuente que exige un alto nivel de sofisticación y autonomía en su modelo de control de código fuente.

 ![Información general sobre el control de código fuente](../../extensibility/internals/media/sourcectnrloverview.gif "SourceCtnrlOverview")

## <a name="source-control-plug-in"></a>Complemento control de código fuente
 Todas las versiones de Visual Studio admiten la especificación de api de complemento de Control de código fuente versión 1.2 como una ruta de acceso de integración. Un implementador de complemento de control de código fuente escribe un archivo DLL que implementa las funciones de la API de complemento de Control de código fuente para la integración y el registro del control de código fuente, tal como se describe en Creación de [un complemento](../../extensibility/internals/creating-a-source-control-plug-in.md)de control de código fuente . En este enfoque, el entorno de desarrollo [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] integrado (IDE) usa la interfaz de usuario para los cuadros de diálogo, como la protección, la desprotección, las páginas de propiedades de herramientas/opciones, las barras de herramientas y los glifos de control de código fuente. La estricta adherencia a la API de complemento de Control de código fuente asegura una fácil integración en Visual Studio y una experiencia sin problemas para el usuario. Esto significa que el complemento de control de código fuente debe implementar la mayoría de las funciones y devoluciones de llamada detalladas en la API.

 Para implementar un complemento de control de código fuente mediante la API de complemento de Control de código fuente, siga estos pasos:

1. Cree un archivo DLL que implemente las funciones especificadas en [Complementos](../../extensibility/source-control-plug-ins.md)de Control de código fuente .

2. Registre el archivo DLL realizando las entradas de registro adecuadas (descritas en [Cómo: instalar un complemento](../../extensibility/internals/how-to-install-a-source-control-plug-in.md)de Control de código fuente ).

3. Crear una interfaz de usuario auxiliar y mostrar cuando se le solicite el paquete de adaptador de Control de código fuente (el componente de Visual Studio que controla la funcionalidad de control de código fuente a través de complementos de control de código fuente)

   En respuesta a un comando de control de código fuente, el IDE de Visual Studio presenta una interfaz de usuario estándar para las operaciones básicas y, a continuación, pasa la información al complemento de control de código fuente a través de las funciones definidas en la API de complemento de Control de código fuente. Para las opciones avanzadas, se puede llamar al complemento de control de código fuente para presentar su propia interfaz de usuario, por ejemplo, la exploración de un proyecto controlado por código fuente. Esto significa que al usuario se le pueden presentar dos estilos posiblemente diferentes de la interfaz de usuario al tratar con el control de código fuente: la interfaz de usuario que presenta Visual Studio y la interfaz de usuario que presenta el complemento de control de código fuente. Esto es más notable con las operaciones avanzadas de control de código fuente.

### <a name="drawbacks-to-implementing-a-source-control-plug-in"></a>Inconvenientes para implementar un complemento de control de código fuente

- Para las características avanzadas, el usuario puede ver dos estilos diferentes de interfaces, lo que conduce a una posible confusión.

- El complemento de control de código fuente se limita al modelo de control de código fuente implicado por la API de complemento de Control de código fuente.

- La API de complemento de Control de código fuente puede ser demasiado restrictiva para algunos escenarios de control de código fuente.

### <a name="advantages-to-implementing-a-source-control-plug-in"></a>Ventajas de implementar un complemento de control de código fuente

- Visual Studio proporciona toda la interfaz de usuario para todas las operaciones básicas de control de código fuente para que el complemento de control de código fuente no tenga que implementar una interfaz de usuario potencialmente compleja.

- Debido a la API estricta, el complemento de control de código fuente puede interactuar fácilmente con programas de control de código fuente externos para proporcionar una funcionalidad más extensa; A Visual Studio no le importa demasiado cómo se logra la funcionalidad del control de código fuente, solo que se realiza de acuerdo con la API de complemento de Control de código fuente.

- Es más fácil implementar un complemento de control de código fuente que un control de código fuente VSPackage.

## <a name="source-control-vspackage"></a>Control de código fuente VSPackage
 [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]permite una integración profunda en Visual Studio con control total de la funcionalidad de control de código fuente y reemplazo completo de la interfaz de usuario de control de código fuente proporcionada por Visual Studio. Un control de código fuente VSPackage se registra con Visual Studio y proporciona funcionalidad de control de código fuente. Aunque varios VSPackages de control de código fuente se pueden registrar con Visual Studio, solo uno de ellos puede estar activo en cualquier momento. Un control de código fuente VSPackage tiene control total sobre la funcionalidad y la apariencia del control de código fuente en Visual Studio mientras está activo. Todos los demás VSPackages de control de código fuente que se pueden registrar en el sistema están inactivos y no mostrará ninguna interfaz de usuario en absoluto.

 Implementar un control de código fuente VSPackage requiere una estrategia de "todo o nada". El creador de un control de código fuente VSPackage debe invertir una cantidad significativa de esfuerzo en la implementación de un número de interfaces de control de código fuente y nuevos elementos de interfaz de usuario (cuadros de diálogo, menús y barras de herramientas) para cubrir toda la funcionalidad de control de código fuente. Consulte [crear un VSPackage de control de código fuente](../../extensibility/internals/creating-a-source-control-vspackage.md) para obtener más detalles.

### <a name="drawbacks-to-implementing-a-source-control-vspackage"></a>Inconvenientes para implementar un control de código fuente VSPackage

- El VSPackage debe implementar una serie de interfaces complejas para integrar se integran correctamente con Visual Studio.

- El VSPackage debe proporcionar toda la interfaz de usuario necesaria para el control de código fuente; Visual Studio no proporcionará asistencia en esta área.

- Un control de código fuente VSPackage está íntimamente vinculado a Visual Studio y no puede funcionar con programas independientes, por lo que la funcionalidad no se puede compartir tan fácilmente con una versión externa del programa de control de código fuente.

### <a name="advantages-to-implementing-a-source-control-vspackage"></a>Ventajas de implementar un control de código fuente VSPackage

- Dado que el VSPackage tiene control total sobre la interfaz de usuario y la funcionalidad del control de código fuente, el usuario se presenta con una interfaz perfecta para el control de código fuente.

- El VSPackage no se limita a un modelo de control de código fuente determinado.

## <a name="see-also"></a>Vea también
- [Control de código fuente](../../extensibility/internals/source-control.md)
- [Creación de un complemento de control de código fuente](../../extensibility/internals/creating-a-source-control-plug-in.md)
- [Creación de un VSPackage de control de código fuente](../../extensibility/internals/creating-a-source-control-vspackage.md)
- [Novedades del control de código fuente](../../extensibility/internals/what-s-new-in-source-control.md)
