---
title: "Glosario del depurador de Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Glosario [SDK de depuración]"
  - "depurar [SDK de depuración], Glosario"
ms.assetid: 4a2cfaab-1fbd-4a23-bd00-9ac4cc50d7fd
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# Glosario del depurador de Visual Studio
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Los siguientes son términos utilizados en [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] de depuración SDK.  
  
## términos  
 punto de interrupción enlazado  
 una abstracción para un punto de interrupción establecido en código.  Existe una relación uno a uno entre un punto de interrupción enlazado y una instrucción de punto de interrupción en la secuencia de código.  Cuando el código descarga, los puntos de interrupción enlazados pueden desenlazar.  
  
 causalidad  
 Proporciona la capacidad de seguir un subproceso lógico de ejecución entre subprocesos, de los procesos, y de varios equipos físicos, y volver a crear la pila de llamadas del subproceso lógico en cualquier punto determinado de la duración de dicho subproceso.  
  
 contexto del código  
 Proporciona una abstracción de una posición en el código del motor de depuración.  Para la mayoría de las arquitecturas en tiempo de ejecución, un contexto de código es una dirección en una secuencia de instrucciones de programa.  Para los lenguajes no tradicionales, en los que el código no se puede representar mediante instrucciones, un contexto de código puede representarse por otros medios.  
  
 ruta de acceso de código  
 Representa un punto de la ejecución del código donde se toma una bifurcación o se realiza una llamada de función.  Un seguimiento de la pila es básicamente una lista de rutas de acceso del código de llamada de función.  
  
 motor de depuración \(DE\)  
 Un componente que permite la depuración de una arquitectura en tiempo de ejecución.  Un motor de depuración funciona junto con el intérprete o el sistema operativo y proporciona servicios de depuración como control de ejecución, puntos de interrupción, y evaluación de la expresión.  
  
 contexto del documento  
 Proporciona una abstracción de una posición en un documento del archivo de código fuente del motor de depuración.  Para la mayoría de los lenguajes, un contexto de documento es una posición en un archivo de código fuente.  Para los lenguajes no tradicionales, para el que el archivo de código fuente puede no ser texto, un contexto de documento puede representarse por otros medios.  vea también el *documento colocar*.  
  
 posición del documento  
 Proporciona una abstracción de una posición en un archivo de código fuente conocido al IDE.  Para la mayoría de los lenguajes, una posición de documento es una posición en un archivo de código fuente.  Para los lenguajes no tradicionales, una posición de documento puede representarse de otras maneras.  Vea también *el contexto del documento*.  
  
 punto de interrupción de error  
 una abstracción para describir un error en un punto de interrupción pendiente.  Un punto de interrupción de error puede describir un error en la ubicación del punto de interrupción pendiente, la expresión asociado al punto de interrupción pendiente, u otra información que evita el punto de interrupción pendiente de enlace a una ubicación del código.  
  
 contexto de evaluación  
 Proporciona una abstracción de un contexto de programación para la evaluación de la expresión.  Normalmente, un contexto de evaluación es un ámbito.  Al hacer la evaluación de expresiones en un contexto de expresiones, el contexto de expresiones proporciona las reglas de ámbito que coincidan con el punto de creación.  Por ejemplo, un contexto de expresiones creado en un marco de pila proporcionará el contexto para las variables locales, los parámetros de método, los miembros de clase \(si procede\), y las variables globales de evaluación.  
  
 excepción intercepta  
 Una excepción que es interceptada por un motor de depuración, incluso si no hay ningún mecanismo de control de excepciones en el marco de pila actual.  
  
 JustMyCode  
 El concepto de depurar sólo el código correspondiente a un usuario y a omitir todo el código intermedio como sistema código\-uniforme si el código fuente disponible para el código del sistema.  
  
 hasta que finalice el punto de interrupción  
 Proporciona una abstracción para los puntos de interrupción antes, durante y, a continuación del código se carga y una forma de virtualizar puntos de interrupción.  un punto de interrupción pendiente:  
  
-   Contiene toda la información necesaria para enlazar un punto de interrupción al código en uno o más programas.  
  
-   Enlace de mayo a las varias ubicaciones del código en uno o más programas.  
  
-   Nunca se enlaza al código.  
  
 Cada vez que se carga el código, todos los puntos de interrupción pendientes en un programa se comprueban para ver si pueden enlazar.  Un punto de interrupción pendiente se dice que contener todos los puntos de interrupción enlazados que enlaza.  
  
 proceso  
 un proceso físico de Win32.  Un proceso puede contener varios programas.  Vea también *el programa*.  
  
 programa  
 Una única ejecución de espacio de nombres dentro de una arquitectura determinada en tiempo de ejecución.  Vea también *el proceso*.  
  
 administrador de depuración de sesión \(SDM\)  
 Administra cualquier número de motores de depuración de depuración cualquier número de programas en varios procesos en cualquier número de equipos.  En el nivel básico, el SDM es un multiplexor de los motores de depuración.  Además, el SDM proporciona una vista unificada la sesión de depuración al IDE.  
  
 marco de pila  
 Representa el estado del cálculo en un cuadro y un detalle determinados nivel de llamadas a funciones anidadas.  
  
 Subproceso  
 La noción generalizada de ejecución pila\-basado de la ejecución de la instrucción en al menos un programa.  
  
 punto de interrupción de advertencia  
 una abstracción para describir una advertencia en un punto de interrupción pendiente.  Un punto de interrupción de advertencia describe una razón por la que el punto de interrupción pendiente aún no ha enlazado a una ubicación del código.  Puede ser que el código no ha cargado todavía para la ubicación descrita por el punto de interrupción pendiente, o por algún otro motivo.  
  
## Vea también  
 [Extensibilidad del depurador de Visual Studio](../../../extensibility/debugger/visual-studio-debugger-extensibility.md)