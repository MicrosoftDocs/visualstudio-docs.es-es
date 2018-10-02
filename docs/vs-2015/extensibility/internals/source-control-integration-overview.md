---
title: Información general sobre la integración de Control de origen | Documentos de Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- source control [Visual Studio SDK], about source control
ms.assetid: 3a46e4eb-e677-49c3-8647-d927d035a19a
caps.latest.revision: 17
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ca8fc2368fd2da031342cf76ab7ba9abb85e6f4b
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47577986"
---
# <a name="source-control-integration-overview"></a>Información general de la integración del control de código fuente
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [información general sobre la integración de Control de código fuente](https://docs.microsoft.com/visualstudio/extensibility/internals/source-control-integration-overview).  
  
Esta sección comparan las dos maneras de integrar en el control de código fuente de Visual Studio; control de origen de un complemento y un VSPackage que proporciona una solución de control de código fuente y se resalta las nuevas características de control de código fuente. Visual Studio permite la conmutación manual entre VSPackages de control de código fuente y los complementos de control de código fuente, así como cambio automático basado en la solución.  
  
## <a name="source-control-integration"></a>Integración de Control de código fuente  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] admite dos tipos de opciones de integración de control de código fuente. En todas las versiones de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], aún podrá integrar un complemento basado en el origen de complemento de API de Control (anteriormente también conoce como la API de MSSCCI), que proporciona funcionalidad de control de código fuente básicos al usar Visual Studio origen (de interfaz de usuario de control INTERFAZ DE USUARIO). Un control de código fuente VSPackage, por otro lado, proporciona una nueva, integración profunda [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] ruta de acceso adecuado para la integración de control de código fuente que exige un alto nivel de sofisticación y autonomía en su modelo de control de código fuente.  
  
 ![Información general del Control de origen](../../extensibility/internals/media/sourcectnrloverview.gif "SourceCtnrlOverview")  
  
## <a name="source-control-plug-in"></a>Complemento de Control de código fuente  
 Todas las versiones de Visual Studio admiten la API de complementos de Control de la versión 1.2 de la especificación de origen como una ruta de acceso de integración. Un implementador de complemento de control de origen escribe un archivo DLL que implementa las funciones de API de complemento de Control de código fuente para integración de control de código fuente y el registro como se describe en [crear un complemento de Control de código fuente](../../extensibility/internals/creating-a-source-control-plug-in.md). En este enfoque, el entorno de desarrollo integrado (IDE) utiliza el [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] interfaz de usuario para los cuadros de diálogo, como la protección, la desprotección, páginas de propiedades de herramientas/opciones, las barras de herramientas y glifos de control de código fuente. Cumplimiento estricto de la API de complemento de Control de código fuente garantiza una integración fácil en Visual Studio y una experiencia sin problemas para el usuario. Esto significa que el complemento de control de origen debe implementar la mayoría de las funciones y las devoluciones de llamada que se detalla en la API.  
  
 Para implementar un complemento mediante la API de complemento de Control de código fuente de control de código fuente, siga estos pasos:  
  
1.  Crear un archivo DLL que implementa las funciones especificadas en [de complementos de Control de código fuente](../../extensibility/source-control-plug-ins.md).  
  
2.  Registrar la DLL mediante la realización de las entradas del Registro adecuados (se describe en [Cómo: instalar un complemento de Control de código fuente](../../extensibility/internals/how-to-install-a-source-control-plug-in.md)).  
  
3.  Crear una aplicación auxiliar de la interfaz de usuario y la presentación cuando se lo solicite el paquete de adaptador de Control de código fuente (el componente de Visual Studio que controla la funcionalidad de control de código fuente a través de los complementos de control de código fuente)  
  
 En respuesta a un comando de control de código fuente, el IDE de Visual Studio presenta una interfaz de usuario estándar para las operaciones básicas y, a continuación, pasa la información para el control de código fuente complemento a través de las funciones definidas en la API de complemento de Control de código fuente. Para las opciones avanzadas, el complemento de control de código fuente puede llamarse en para presentar su propia interfaz de usuario, por ejemplo, para un proyecto de control de código fuente de exploración. Esto significa que el usuario puede aparecer dos estilos posiblemente diferentes de interfaz de usuario cuando se trabaja con control de código fuente: la interfaz de usuario que presenta Visual Studio y la interfaz de usuario que presenta el complemento de control de código fuente. Esto resulta especialmente patente con las operaciones de control de código fuente avanzados.  
  
### <a name="drawbacks-to-implementing-a-source-control-plug-in"></a>Inconvenientes para implementar un complemento de Control de código fuente  
  
-   Para las características avanzadas, el usuario puede ver dos estilos diferentes de las interfaces, dando lugar a confusión posible.  
  
-   El complemento de control de código fuente se limita al modelo de control de código fuente implicado en la API de complemento de Control de código fuente.  
  
-   La API de complemento de Control de origen puede ser demasiado restrictiva para algunos escenarios de control de código fuente.  
  
### <a name="advantages-to-implementing-a-source-control-plug-in"></a>Ventajas de implementar un complemento de Control de código fuente  
  
-   Visual Studio proporciona toda la interfaz de usuario para todas las operaciones de control de código fuente básicos para que el complemento de control de origen no tiene que implementar la interfaz de usuario potencialmente complejo.  
  
-   Debido a la API estricto, el complemento de control de código fuente puede interactuar fácilmente con programas de control de origen externo para proporcionar funcionalidad más extensa; Visual Studio no le importa demasiado mucho cómo se consigue la funcionalidad de control de código fuente, solo que se lleva a cabo según la API de complemento de Control de código fuente.  
  
-   Es más fácil de implementar un complemento que un VSPackage de control de código fuente de control de código fuente.  
  
## <a name="source-control-vspackage"></a>VSPackage de Control de código fuente  
 [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] permite una integración profunda en Visual Studio con control total sobre la funcionalidad de control de código fuente y de reemplazo completo de la interfaz de usuario de control de origen proporcionada por Visual Studio. Un control de código fuente VSPackage está registrado con Visual Studio y proporciona la funcionalidad de control de código fuente. Aunque varios VSPackages de control de código fuente se puede registrar con Visual Studio, solo uno de ellos puede estar activo en cualquier momento. Un VSPackage de control de código fuente tiene control total sobre la funcionalidad de control de código fuente y la apariencia de Visual Studio cuando está activo. Todos los otro VSPackages que se puede registrar en el sistema de control de código fuente están inactiva y no mostrará ninguna interfaz de usuario en absoluto.  
  
 Implementación de un VSPackage de control de código fuente, requiere una estrategia de "todo o nada". El creador de un VSPackage de control de código fuente debe invertir una cantidad considerable de esfuerzo en la implementación de una serie de interfaces del control de código fuente y los nuevos elementos de interfaz de usuario (cuadros de diálogo, menús y barras de herramientas) para cubrir la funcionalidad de control de código fuente. Consulte [crear un VSPackage de Control de código fuente](../../extensibility/internals/creating-a-source-control-vspackage.md) para obtener más detalles.  
  
### <a name="drawbacks-to-implementing-a-source-control-vspackage"></a>Inconvenientes de la implementación de un VSPackage de Control de código fuente  
  
-   El VSPackage debe implementar un número de interfaces complejas para una integración correcta con Visual Studio.  
  
-   El VSPackage debe proporcionar toda la interfaz de usuario necesario para el control de código fuente; Visual Studio no proporcionará ninguna asistencia en esta área.  
  
-   Un control de código fuente VSPackage está estrechamente vinculado a Visual Studio y no puede funcionar con programas independientes, por lo que no se puede compartir fácilmente la funcionalidad con una versión del programa de control de origen externa.  
  
### <a name="advantages-to-implementing-a-source-control-vspackage"></a>Ventajas de implementar un VSPackage de Control de código fuente  
  
-   Dado que el VSPackage tiene funcionalidad y control total sobre el control de código fuente de la interfaz de usuario, se presenta al usuario con una interfaz transparente para el control de código fuente.  
  
-   El VSPackage no se limita a un modelo de control de código fuente concreto.  
  
## <a name="see-also"></a>Vea también  
 [Control de código fuente](../../extensibility/internals/source-control.md)   
 [Creación de un Control de código fuente complemento](../../extensibility/internals/creating-a-source-control-plug-in.md)   
 [Creación de un VSPackage de Control de código fuente](../../extensibility/internals/creating-a-source-control-vspackage.md)   
 [Novedades del control de código fuente](../../extensibility/internals/what-s-new-in-source-control.md)

