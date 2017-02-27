---
title: "Visual Studio Shell (integrado) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Características de shell el modo integrado de Visual Studio"
  - "Características del modo integrado el shell [Visual Studio]"
ms.assetid: 0b40d495-f17f-4bb9-ace8-b365a7172784
caps.latest.revision: 26
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 26
---
# Visual Studio Shell (integrado)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

El shell integrado de Visual Studio incluye el entorno de desarrollo integrado \(IDE\), el depurador y la integración de control de código fuente. No se incluye ningún lenguaje de programación. Sin embargo, el shell integrado proporcionan un marco que permite agregar los lenguajes de programación.  
  
 El shell integrado de Visual Studio es realmente una combinación de shell de Visual Studio aislada más una instalación adicional que incluir componentes específicos de shell integrado.  La aplicación de shell integrado debe incluir tanto el shell aislado paquete redistribuible de [paquete redistribuible de Microsoft Visual Studio Shell \(aislado\)](http://go.microsoft.com/fwlink/?LinkId=616022) así como el paquete redistribuible de shell integrado de [paquete redistribuible de Microsoft Visual Studio Shell \(integrado\)](http://go.microsoft.com/fwlink/?LinkId=616021).  
  
> [!NOTE]
>  Antes de poder acceder a los paquetes redistribuibles de shell aislado e integrado, deberá rellenar una encuesta a clientes breve.  Después de rellenar la encuesta, le dirige a la página Conectar de Visual Studio con vínculos de descarga del paquete redistribuible.  Puede encontrar los vínculos de descarga en visitas posteriores al sitio Visual Studio Connect en el **programas &#124; VISUAL STUDIO 2015 y aislado SHELL integrado** ficha.  
  
 Si instala la aplicación de shell integrada en el mismo equipo que una versión completa de Visual Studio, componentes de la aplicación se integrarán directamente en Visual Studio.  
  
## Características en el Shell integrado  
  
|||  
|-|-|  
|Área de características|Característica|  
|Compatibilidad con idiomas|-   Ninguna|  
|IDE|<ul><li>Configuración<br /><br /> <ul><li>Crear una configuración</li><li>Importar y exportar configuraciones</li><li>Restablecer la configuración</li></ul></li><li>**Herramientas** integración</li><li>**Lista de tareas** integración</li><li>Integración de ayuda</li><li>**Opciones** cuadro de diálogo</li><li>Administración de fuentes y colores</li><li>**Salida** ventana</li><li>**Comando** ventana</li><li>Administración de ventanas</li><li>Enlaces de teclado, menús y comandos</li><li>En tiempo de ejecución de lenguaje específico de dominio \(DSL\)</li></ul>|  
|Sistema de proyectos y tipos de proyecto|-   Soluciones y las carpetas de soluciones<br />-   Administrador de configuración de la solución<br />-   Administración de elementos<br />-   Soluciones de proyecto único y varios proyectos<br />-   Diseñador de aplicaciones \(propiedades del proyecto simplificado\)<br />-   Agregar referencia web<br />-   Agregar referencia de servicio<br />-   Proyecto único<br />-   Tipos de proyecto de sitio Web<br />-   Proyectos de aplicación Web|  
|Compilar|-   Los pasos de compilación personalizada de IDE<br />-   Precompilación para la protección de propiedad intelectual \(IP\)<br />-   Firma de código<br />     MSBuild|  
|Editor de|-   Código examinar herramientas \(búsqueda unificada, definición de origen, herencia\)<br />-   Navegación por el código<br />-   IntelliSense<br />-   Etiquetas inteligentes<br />-   Refactorización<br />-   Lista descriptiva<br />-   Filtrado de IntelliSense<br />-   **Definición de código** ventana|  
|Designer|-   Diseñador de Windows Presentation Foundation<br />-   Diseñador de Windows Forms<br />-   Editor HTML y Diseñador Web|  
|Datos|-   **Server Explorer** \(simplificado: sólo los datos\). Vea la Nota 1.<br />-   **Orígenes de datos** ventana<br />-   Conjunto completo de controles de datos<br />-   Editor XML<br />-   Enlazar datos al origen de datos local \(. MDF o. \(MDB\)<br />-   Objeto de enlace de datos<br />-   Enlazar los datos al servicio Web<br />-   Enlace de datos al servidor de base de datos local<br />-   Enlace de datos al servidor de base de datos remota<br />-   Herramientas DDL para los datos remotos<br />-   **Server Explorer** extensibilidad \([!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] ejemplos\)|  
|Depurador|-   La depuración local. Vea la nota 2.<br />-   Depuración administrada<br />-   Depuración local<br />-   Asociar a proceso local<br />-   Asociar a proceso remoto<br />-   Delegado anónimo<br />-   Dominios de aplicación<br />-   Depuración ASPX<br />-   Atributos<br />-   Interrumpir durante la evaluación de Func<br />-   Puntos de interrupción<br />-   Restricciones de punto de interrupción<br />-   Pila de llamadas<br />-   **Comando** ventana<br />-   Depuración entre subprocesos<br />-   Sugerencias de datos<br />-   Visualizador de datos<br />-   Compatibilidad del depurador con asistentes para la depuración administradas \(MDA\)<br />-   Compatibilidad del depurador para el reenviador de tipos<br />-   Compatibilidad con DTEEvents OTB<br />-   JMC paso a paso<br />-   Prueba de AppID de depurador \(DBGCLR\)<br />-   Perfil del depurador<br />-   Opciones y herramientas del depurador<br />-   Iterador de depuración<br />-   Evaluación de expresiones en tiempo de diseño<br />-   Evaluador de expresiones de C\#<br />-   Desensamblado<br />-   Editar y continuar<br />-   Ventanas del evaluador de expresiones \(inspección, variables locales, automático\)<br />-   Aplicación auxiliar de excepciones<br />-   Excepciones<br />-   Execution<br />-   Genéricos<br />-   Obtener origen derecha<br />-   Depurador de clúster HPC<br />-   Depuración de varios idiomas integrada<br />-   Depuración de interoperabilidad<br />-   Depuración Just\-in\-time<br />-   Depuración local<br />-   Depuración administrada<br />-   Control manual \(ventana de procesos\)<br />-   Memoria<br />-   Soporte de minivolcado<br />-   Módulos<br />-   Depuración multiproceso<br />-   Nativo de depuración<br />-   Nueva compatibilidad de motor de depuración<br />-   Depurar código optimizado<br />-   Filtrado de windows de salida<br />-   Proceso de hospedaje para la depuración administrada<br />-   Procesos<br />-   Inspección rápida<br />-   Registros<br />-   Registros de pila<br />-   Depuración remota<br />-   Valores devueltos<br />-   Depuración de script<br />-   Soporte de servicio de origen<br />-   Seguridad<br />-   Side\-by\-side<br />-   SQL<br />-   Servidor de símbolos<br />-   Puntos de seguimiento<br />-   Subproceso<br />-   Visualizaciones<br />-   Depurador Extensible Stylesheet Language Transformations \(XSLT\)|  
|compatibilidad con 64 bits|-   depuración de código administrado y nativo, todos los idiomas de 64 bits<br />-   compatibilidad con x 64 nativo|  
|Control de código fuente \(SCC\)|-   Integración básica de control de código fuente. Vea la nota 3.<br />-   Herramientas y opciones de comprobación|  
|Extensibilidad|-   Consumir componentes VSPackages y MEF|  
  
## Notas  
  
#### 1. Herramientas de datos  
 El shell integrado incluye herramientas de desarrollo de base de datos como la compatibilidad de extensibilidad de datos y simplificado **el Explorador de soluciones**. Sin embargo, SQL Server Express, SQL Reporting y Crystal Reports no se incluyen en el shell integrado.  
  
#### 2. Capacidad de depuración  
 El shell integrado incluye el mismo motor de depuración que se incluye en la versión de Visual Studio. El motor de depuración incluye al depurador común para código administrado así como características relacionadas, como ejecutar, adjuntar, establecer punto de interrupción, editar y continuar y otros. Sin embargo, el motor de depuración no admite la depuración de base de datos de SQL Server.  
  
 Aunque admite la depuración nativa está incluida en el paquete básico del depurador, no se puede extender para admitir idiomas adicionales.  
  
#### 3. Integración del Control de código fuente  
 El shell integrado proporciona las API para implementar el control de código fuente \(SCC\) y para proporcionar el control de código fuente común basada en MSSCCI componentes de integración.  
  
 Aunque la integración del control de código fuente no es una característica habitual de la edición Pro de Visual Studio, la integración de SCC se proporciona en el shell integrado.  
  
#### 4. Compatibilidad de compilación  
 El shell integrado proporciona compatibilidad con la compilación. Puede encontrar información sobre las compilaciones en la [Referencia de MSBuild](../msbuild/msbuild-reference.md).  
  
## Características no incluidas en el Shell integrado  
 La siguiente es una lista de características que no están incluidos en el shell integrado:  
  
-   Diseñador de clases  
  
-   DotFuscator preferente  
  
-   Características del lenguaje  
  
-   VSHost  
  
-   Ningún idioma de Visual Studio o sus plantillas de proyecto asociado o plantillas de elemento de proyecto, se incluyen en el shell integrado. Implementaciones específicas del idioma de otras características no se incluyen para fragmentos de código de Visual Basic de ejemplo.  
  
## Vea también  
 [Información general sobre la extensión de Visual Studio](../Topic/Extending%20Visual%20Studio%20Overview.md)