---
title: "Informaci&#243;n general sobre la integraci&#243;n de Control de c&#243;digo fuente | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "control de código fuente [Visual Studio SDK], acerca de control de código fuente"
ms.assetid: 3a46e4eb-e677-49c3-8647-d927d035a19a
caps.latest.revision: 16
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 16
---
# Informaci&#243;n general sobre la integraci&#243;n de Control de c&#243;digo fuente
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

esta sección compara las dos maneras de integrar en el control de código fuente de Visual Studio; un complemento de control de código fuente y un VSPackage que proporciona una solución de control de código fuente y resalta las nuevas características de control de código fuente.  Visual Studio permite conmutación manual entre el control de código fuente VSPackages y complementos de control de código fuente así como cambiar solución\-basada automática.  
  
## Integración del control de código fuente  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] admite dos tipos de opciones de integración de control de código fuente.  En todas las versiones de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], todavía puede integrar un complemento basado en el complemento de control de código fuente API \(previamente incluirse el MSSCCI API\), que proporciona la funcionalidad básica de control de código fuente mientras utiliza la interfaz de usuario del control de código fuente de Visual \(UI\) Studio.  Un control de código fuente VSPackage, por otro lado, proporciona un nuevo, la ruta de [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] de la profundo\-integración adecuado para la integración del control de código fuente que requiera un nivel alto de la sofisticación y la autonomía en el modelo de control de código fuente.  
  
 ![Información general sobre el control de código fuente](~/extensibility/internals/media/sourcectnrloverview.gif "SourceCtnrlOverview")  
  
## complemento de control de código fuente  
 Todas las versiones de Visual Studio admiten la versión de la especificación de la API del complemento de control de código fuente 1,2 como ruta de integración.  Un implementador del complemento de control de código fuente escribe un archivo DLL que implementa las funciones API del complemento de control de código fuente para la integración y el registro del control de código fuente como se describe en [Creación de un Control de origen de complemento](../../extensibility/internals/creating-a-source-control-plug-in.md).  En este enfoque, el entorno de \(IDE\) desarrollo integrado \(IDE\) utiliza la interfaz de usuario de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] para los cuadros de diálogo, como la protección, comprobación, herramientas y páginas de propiedades de opciones, barras de herramientas, y glifos de control de código fuente.  La adherencia estricta al complemento de control de código fuente API garantiza una integración sin en Visual Studio y una experiencia sin problemas para el usuario.  Esto significa que el complemento de control de código fuente debe implementar la mayoría de las funciones y las devoluciones de llamada detallados en la API.  
  
 Para implementar un complemento de control de código fuente utilizando el complemento de control de código fuente API, siga estos pasos:  
  
1.  Cree un archivo DLL que implementa las funciones especificadas en [Complementos de Control de código fuente](../../extensibility/source-control-plug-ins.md).  
  
2.  Registre la DLL creando las entradas de Registro adecuadas \(descritas en [Cómo: instalar un complemento de Control de código fuente](../../extensibility/internals/how-to-install-a-source-control-plug-in.md)\).  
  
3.  Cree una interfaz de usuario de la aplicación auxiliar y muestre cuando se le pregunte por el paquete de adaptador de control de código fuente \(el componente de Visual Studio que controla la funcionalidad de control de código fuente mediante complementos de control de código fuente\)  
  
 En respuesta a un comando de control de código fuente, el IDE de Visual Studio muestra una interfaz de usuario estándar para las operaciones básicas y pasa la información al complemento de control de código fuente mediante las funciones definidas en el complemento de control de código fuente API.  Para las opciones avanzadas, el complemento de control de código fuente se puede llamar para mostrar su propia interfaz de usuario, por ejemplo, buscar un proyecto bajo control de código fuente.  Esto significa que el usuario puede mostrar con dos posiblemente diferentes estilos de la interfaz de usuario cuando se trata con el control de código fuente: la interfaz de usuario que Visual Studio muestra y la interfaz de usuario que el complemento de control de código fuente muestra.  Esto resulta especialmente patente con operaciones de control de código fuente avanzado.  
  
### desventajas a implementar un complemento de control de código fuente  
  
-   Para las características avanzadas, puede ver dos estilos diferentes de interfaces, dando lugar a confusión posible.  
  
-   El complemento de control de código fuente se restringe al modelo de control de código fuente implícitamente en el complemento de control de código fuente API.  
  
-   El complemento de control de código fuente API puede ser demasiado restrictivo para algunos escenarios de control de código fuente.  
  
### ventajas a implementar un complemento de control de código fuente  
  
-   Fuentes de Visual Studio toda la interfaz de usuario para todas las operaciones de control de código fuente básicas de modo que el complemento de control de código fuente no tiene que implementar interfaz de usuario probablemente compleja.  
  
-   Debido a la API estricta, el complemento de control de código fuente puede interactuar fácilmente con programas de control de código fuente externo para proporcionar una funcionalidad más extensa; Visual Studio no interesen demasiado cómo la funcionalidad de control de código fuente se consigue, sólo que se consigue según el complemento de control de código fuente API.  
  
-   Es más fácil de implementar un complemento de control de código fuente que un control de código fuente VSPackage.  
  
## control de código fuente VSPackage  
 [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] permite la integración profunda en Visual Studio con el control total de la funcionalidad de control de código fuente y el reemplazo completo de Visual Estudio\-proporcionó a la interfaz de usuario del control de código fuente.  Un control de código fuente VSPackage se registra con Visual Studio y proporciona funcionalidad de control de código fuente.  Aunque varios el control de código fuente VSPackages se puede registrar con Visual Studio, sólo uno de ellos puede estar activo en un momento dado.  Un control de código fuente VSPackage tiene el control completo sobre la funcionalidad y el aspecto del control de código fuente de Visual Studio mientras está activo.  El resto del control de código fuente VSPackages que se puede registrar en el sistema está inactivo y no mostrará ninguna interfaz de usuario en absoluto.  
  
 implementar un control de código fuente VSPackage no requiere un “todo o nada” estrategia.  El creador de un control de origen VSPackage debe invertir un esfuerzo significativo en implementar varias interfaces de control de código fuente y nuevos elementos de la interfaz de usuario \(cuadros de diálogo, menús, y barras de herramientas\) para cubrir toda la funcionalidad del control de código fuente.  Vea [Crear un VSPackage del Control de código fuente](../../extensibility/internals/creating-a-source-control-vspackage.md) para obtener más información.  
  
### desventajas a implementar un control de código fuente VSPackage  
  
-   El Paquete debe implementar varias interfaces complejas para integrar correctamente con Visual Studio.  
  
-   El Paquete debe proporcionar toda la interfaz de usuario necesaria para el control de código fuente; Visual Studio no proporciona ninguna ayuda en esta área.  
  
-   Un control de código fuente VSPackage está enlazada más interno a Visual Studio y no puede ejecutar programas independientes, por lo que la funcionalidad no puede estar como fácilmente compartido con una versión externa del control de código fuente.  
  
### ventajas a implementar un control de código fuente VSPackage  
  
-   Dado que el Paquete tiene el control completo sobre la interfaz de usuario y la funcionalidad de control de código fuente, se presenta al usuario una interfaz sin problemas para el control de código fuente.  
  
-   El Paquete no se restringe a un modelo de control de código fuente concreto.  
  
## Vea también  
 [Control de código fuente](../../extensibility/internals/source-control.md)   
 [Creación de un Control de origen de complemento](../../extensibility/internals/creating-a-source-control-plug-in.md)   
 [Crear un VSPackage del Control de código fuente](../../extensibility/internals/creating-a-source-control-vspackage.md)   
 [Novedades de Control de código fuente](../../extensibility/internals/what-s-new-in-source-control.md)