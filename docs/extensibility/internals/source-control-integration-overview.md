---
title: Descripción de la integración de Control de origen | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], about source control
ms.assetid: 3a46e4eb-e677-49c3-8647-d927d035a19a
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 19d75936e21729729dfeafaa041d800acbe01caa
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="source-control-integration-overview"></a>Información general sobre la integración de Control de código fuente
Esta sección comparan las dos maneras de integrar en control de código fuente de Visual Studio; un control de código fuente complemento y un VSPackage que proporciona una solución de control de código fuente y resalta las nuevas características de control de código fuente. Visual Studio permite la conmutación manual entre el control de código fuente VSPackages y los complementos de control de código fuente, así como basados en soluciones cambiar de forma automática.  
  
## <a name="source-control-integration"></a>Integración del Control de código fuente  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] admite dos tipos de opciones de integración de control de código fuente. En todas las versiones de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], aún podrá integrar un complemento basado en el origen de Control API de complementos (anteriormente también denominados MSSCCI API), que proporciona funcionalidad de control de código fuente básico al usar Visual Studio origen (de interfaz de usuario de control INTERFAZ DE USUARIO). Un control de código fuente VSPackage, por otro lado, proporciona una integración profunda nueva, [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] ruta de acceso adecuado para la integración de control de código fuente que requiere un alto nivel de sofisticación y autonomía en su modelo de control de origen.  
  
 ![Información general del Control de origen](../../extensibility/internals/media/sourcectnrloverview.gif "SourceCtnrlOverview")  
  
## <a name="source-control-plug-in"></a>Complemento de Control de código fuente  
 Todas las versiones de Visual Studio admiten la API de complementos de Control de la versión 1.2 de la especificación de origen como una ruta de acceso de integración. Un implementador de complemento de control de código fuente escribe un archivo DLL que implementa las funciones de API de complemento de Control de código fuente para la integración del control de código fuente y el registro como se describe en [crear un complemento de Control de código fuente](../../extensibility/internals/creating-a-source-control-plug-in.md). En este enfoque, el entorno de desarrollo integrado (IDE) utiliza el [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] interfaz de usuario para los cuadros de diálogo, como la protección, la desprotección, páginas de propiedades de herramientas/opciones, las barras de herramientas y glifos de control de código fuente. Estricta observancia de la API de complemento de Control de origen garantiza una fácil integración en Visual Studio y una experiencia sin problemas para el usuario. Esto significa que el complemento de control de origen debe implementar la mayoría de las funciones y las devoluciones de llamada que se detallan en la API.  
  
 Para implementar un complemento mediante la API de complemento de Control de origen de control de código fuente, siga estos pasos:  
  
1.  Crear un archivo DLL que implementa las funciones especificadas en [complementos de Control de código fuente](../../extensibility/source-control-plug-ins.md).  
  
2.  Registrar el archivo DLL mediante la realización de las entradas del Registro adecuados (se describe en [Cómo: instalar un complemento de Control de código fuente](../../extensibility/internals/how-to-install-a-source-control-plug-in.md)).  
  
3.  Crear una aplicación auxiliar de interfaz de usuario y la presentación cuando se lo solicite el paquete de adaptador de Control de origen (el componente de Visual Studio que controla la funcionalidad de control de código fuente a través de complementos de control de código fuente)  
  
 En respuesta a un comando de control de código fuente, el IDE de Visual Studio presenta una interfaz de usuario estándar para las operaciones básicas y, a continuación, pasa la información para el control de código fuente complemento a través de las funciones definidas en la API de complementos de Control de código fuente. Para las opciones avanzadas, el complemento de control de código fuente puede llamarse en para presentar su propia interfaz de usuario, por ejemplo, exploración de un proyecto controlado por código fuente. Esto significa que el usuario puede presentarse con dos estilos posiblemente diferentes de interfaz de usuario cuando se trabaja con control de código fuente: la interfaz de usuario que presenta Visual Studio y la interfaz de usuario que presenta el complemento de control de código fuente. Esto resulta más evidente con las operaciones de control de origen avanzado.  
  
### <a name="drawbacks-to-implementing-a-source-control-plug-in"></a>Inconvenientes para implementar un complemento de Control de código fuente  
  
-   Para las funciones avanzadas, el usuario puede ver dos estilos diferentes de las interfaces, dando lugar a posibles confusiones.  
  
-   El complemento de control de código fuente se limita al modelo de control de origen implicado en la API de complementos de Control de código fuente.  
  
-   La API de complemento de Control de origen puede ser demasiado restrictiva para algunos escenarios de control de código fuente.  
  
### <a name="advantages-to-implementing-a-source-control-plug-in"></a>Ventajas de implementar un complemento de Control de código fuente  
  
-   Visual Studio proporciona todas la interfaz de usuario para todas las operaciones de control de código fuente básico para que el complemento de control de origen no tiene que implementar la interfaz de usuario potencialmente compleja.  
  
-   Debido a la API estricta, el complemento de control de código fuente puede interactuar con facilidad con programas de control de origen externo para proporcionar funcionalidad más amplia; Visual Studio no ocupa demasiado mucho cómo se logra la funcionalidad de control de código fuente, solo que se lleva a cabo según la API de complementos de Control de código fuente.  
  
-   Es más fácil de implementar un complemento que un VSPackage del control de código fuente de control de código fuente.  
  
## <a name="source-control-vspackage"></a>Paquete de VS de Control de código fuente  
 [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] permite que integra perfectamente en Visual Studio con el control total de la funcionalidad de control de código fuente y reemplazo completo de la interfaz de usuario de control de código fuente proporcionados por Visual Studio. Un control de código fuente VSPackage se registra con Visual Studio y proporciona la funcionalidad de control de código fuente. Aunque el control de código fuente varios paquetes VSPackage se puede registrar con Visual Studio, sólo uno de ellos pueden activar en cualquier momento. Un control de código fuente VSPackage tiene control total sobre la apariencia y la funcionalidad de control de código fuente en Visual Studio mientras está activa. Todos los otro paquetes VSPackage que puede estar registrada en el sistema de control de código fuente están inactiva y no mostrará ninguna interfaz de usuario en absoluto.  
  
 La implementación de un control de código fuente VSPackage requiere una estrategia de "todo o nada". El creador de un control de código fuente VSPackage debe invertir una considerable cantidad de trabajo en la implementación de una serie de interfaces de control de código fuente y los nuevos elementos de interfaz de usuario (cuadros de diálogo, menús y barras de herramientas) para cubrir la funcionalidad de control de código fuente. Vea [crear un VSPackage de Control de código fuente](../../extensibility/internals/creating-a-source-control-vspackage.md) para obtener más detalles.  
  
### <a name="drawbacks-to-implementing-a-source-control-vspackage"></a>Inconvenientes para implementar un paquete de VS de Control de código fuente  
  
-   El VSPackage debe implementar un número de interfaces complejas para integrar correctamente con Visual Studio.  
  
-   El VSPackage debe proporcionar todas la interfaz de usuario necesaria para el control de código fuente; Visual Studio no proporcionará ninguna asistencia en esta área.  
  
-   Un control de código fuente VSPackage está estrechamente vinculado a Visual Studio y no puede funcionar con programas independientes, por lo que la funcionalidad no se puede compartir fácilmente con una versión del programa de control de origen externa.  
  
### <a name="advantages-to-implementing-a-source-control-vspackage"></a>Ventajas de implementar un paquete de VS de Control de código fuente  
  
-   Dado que el VSPackage tiene funcionalidad y control total sobre la interfaz de usuario de control de código fuente, se presenta al usuario con una interfaz sin problemas de control de código fuente.  
  
-   El VSPackage no se limita a un modelo de control de origen determinado.  
  
## <a name="see-also"></a>Vea también  
 [Control de código fuente](../../extensibility/internals/source-control.md)   
 [Crear un Control de código fuente complemento](../../extensibility/internals/creating-a-source-control-plug-in.md)   
 [Crear un VSPackage de Control de código fuente](../../extensibility/internals/creating-a-source-control-vspackage.md)   
 [Novedades del control de código fuente](../../extensibility/internals/what-s-new-in-source-control.md)