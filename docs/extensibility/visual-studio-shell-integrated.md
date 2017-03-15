---
title: Visual Studio Shell (integrado) | Documentos de Microsoft
ms.custom: 
ms.date: 02/17/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Visual Studio shell, integrated mode features
- Shell [Visual Studio], integrated mode features
ms.assetid: 0b40d495-f17f-4bb9-ace8-b365a7172784
caps.latest.revision: 26
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 4f2ddbc47f9a014acde2850dba5c72ef3a784847
ms.openlocfilehash: 8edd3a6fcca0c2ddd4d580f0874b737cfbbc40c9
ms.lasthandoff: 03/01/2017

---
# <a name="visual-studio-shell-integrated"></a>Visual Studio Shell (integrado)
El shell integrado de Visual Studio incluye el entorno de desarrollo integrado (IDE), el depurador y la integración de control de código fuente. No se incluye ningún lenguaje de programación. Sin embargo, el shell integrado proporcionan un marco que permite agregar los lenguajes de programación.  
  
 El shell integrado de Visual Studio es realmente una combinación de shell de Visual Studio aislada más una instalación adicional que incluir componentes específicos de shell integrado.  La aplicación de shell integrado debe incluir tanto el shell aislado paquete redistribuible de [paquete redistribuible de Microsoft Visual Studio Shell (aislado)](http://go.microsoft.com/fwlink/?LinkId=616022) , así como el paquete redistribuible de shell integrado de [paquete redistribuible de Microsoft Visual Studio Shell (integrado)](http://go.microsoft.com/fwlink/?LinkId=616021).  
  
> [!NOTE]
>  Antes de poder acceder a los paquetes redistribuibles de shell aislado e integrado, deberá rellenar una encuesta a clientes breve.  Después de rellenar la encuesta, le dirige a la página Conectar de Visual Studio con vínculos de descarga del paquete redistribuible.  Puede encontrar los vínculos de descarga en visitas posteriores al sitio Visual Studio Connect en el **programas | VISUAL STUDIO 2015 y aislado SHELL integrado** ficha.  
  
 Si instala la aplicación de shell integrada en el mismo equipo que una versión completa de Visual Studio, componentes de la aplicación se integrarán directamente en Visual Studio.  
  
## <a name="features-in-the-integrated-shell"></a>Características en el Shell integrado  
  
|||  
|-|-|  
|Área de características|Característica|  
|Compatibilidad con idiomas|-Ninguno|  
|IDE|<ul><li>Configuración<br /><br /> <ul><li>Crear una configuración</li><li>Importar y exportar configuraciones</li><li>Restablecer la configuración</li></ul></li><li>**Cuadro de herramientas** integración</li><li>**Lista de tareas** integración</li><li>Integración de ayuda</li><li>**Opciones de** cuadro de diálogo</li><li>Administración de fuentes y colores</li><li>**Salida** ventana</li><li>**Comando** ventana</li><li>Administración de ventanas</li><li>Enlaces de teclado, menús y comandos</li><li>En tiempo de ejecución de lenguaje específico de dominio (DSL)</li></ul>|  
|Sistema de proyectos y tipos de proyecto|-Las soluciones y las carpetas de soluciones<br />: Administrador de configuración de la solución<br />: Administración de elementos<br />-Soluciones proyecto único y varios proyectos<br />-Application Designer (propiedades del proyecto simplificado)<br />-Agregar referencia Web<br />-Agregar referencia de servicio<br />Proyecto único<br />: Tipos de proyecto de sitio Web de<br />: Proyectos de aplicación web|  
|Compilar|-Pasos de compilación personalizada en IDE<br />-La precompilación para la protección de propiedad intelectual (IP)<br />: Firma de código<br />     MSBuild|  
|Editor|-Código examinar herramientas (búsqueda unificada, definición de origen, herencia)<br />: Navegación por el código<br />: IntelliSense<br />-Etiquetas inteligentes<br />-Refactorización<br />-Lista descriptiva<br />: Filtrado de IntelliSense<br />-   **Definición de código** ventana|  
|Diseñador|-Windows Presentation Foundation Designer<br />-Diseñador de formularios de Windows<br />-Editor de HTML y diseñador web|  
|Datos|-   **Explorador de servidores** (simplificado: sólo los datos). Vea la Nota 1.<br />-   **Orígenes de datos** ventana<br />-Todo el conjunto de controles de datos<br />: Editor XML<br />-Datos enlazar al origen de datos local (. MDF o. (MDB)<br />-Enlace de datos de objeto<br />-Enlazar datos al servicio Web<br />-Datos enlazar con el servidor de base de datos local<br />-Datos enlazar con el servidor de base de datos remota<br />-Herramientas DDL para los datos remotos<br />-   **Explorador de servidores** extensibilidad ([!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] ejemplos)|  
|Depurador|-Depuración local. Vea la nota 2.<br />-La depuración administrada<br />-Depuración local<br />-Adjuntar al proceso local<br />-Adjuntar al proceso remoto<br />-Delegado anónimo<br />: Dominios de aplicación<br />: Depuración ASPX<br />: Atributos<br />-Interrumpir durante la evaluación de Func<br />-Los puntos de interrupción<br />: Restricciones de punto de interrupción<br />: Pila de llamadas<br />-   **Comando** ventana<br />-Depuración entre subprocesos<br />: Sugerencias de datos<br />: Visualizador de datos<br />-Compatibilidad del depurador con asistentes para la depuración administradas (MDA)<br />-Compatibilidad con depurador reenviador de tipos<br />-Compatibilidad con DTEEvents OTB<br />-JMC paso a paso<br />-Prueba de AppID depurador (DBGCLR)<br />: Perfil del depurador<br />-Las herramientas y opciones del depurador<br />-Iteradores de depuración<br />-Evaluación de expresiones en tiempo de diseño-de<br />-El evaluador de expresiones C#<br />-Desensamblado<br />-Editar y continuar<br />-Ventanas de evaluador de expresiones de (inspección, variables locales, automático)<br />: Aplicación auxiliar de excepciones<br />: Excepciones<br />-Ejecución<br />-Los genéricos<br />-Obtener origen derecha<br />HPC de clúster<br />-Multilingüe depuración integrada<br />-Depuración de interoperabilidad<br />-Depuración just-in-time<br />-Depuración local<br />-La depuración administrada<br />-Control manual (ventana de procesos)<br />: Memoria<br />-Soporte minivolcado<br />-Módulos<br />-Varios procesos de depuración<br />-Nativo depuración<br />-Nueva compatibilidad de motor de depuración<br />-Depuración de código optimizado<br />-Filtrado de windows output<br />-Proceso de hospedaje para la depuración administrada<br />-Procesos<br />-Inspección rápida<br />: Registros<br />-Registros de pila<br />-Depuración remota<br />: Valores devueltos de<br />: Depuración de script<br />: Compatibilidad de servicio de origen<br />-Seguridad<br />Side-by-side<br />-SQL<br />: Servidor de símbolos<br />: Puntos de seguimiento<br />-Subproceso<br />-Visualizaciones<br />-Depurador de extensible Stylesheet Language Transformations (XSLT)|  
|compatibilidad con&64; bits|-64 bits de depuración para código administrado y nativo, todos los idiomas<br />-admite x64 nativo|  
|Control de código fuente (SCC)|-Integración de SCC básica. Vea la Nota 3.<br />-Las herramientas y opciones de comprobación|  
|Extensibilidad|-Consumir componentes VSPackages y MEF|  
  
## <a name="notes"></a>Notas  
  
#### <a name="1-data-tools"></a>1. Herramientas de datos  
 El shell integrado incluye herramientas de desarrollo de base de datos como la compatibilidad de extensibilidad de datos y simplificado **el Explorador de soluciones**. Sin embargo, SQL Server Express, SQL Reporting y Crystal Reports no se incluyen en el shell integrado.  
  
#### <a name="2-debugging-support"></a>2. Capacidad de depuración  
 El shell integrado incluye el mismo motor de depuración que se incluye en la versión de Visual Studio. El motor de depuración incluye al depurador común para código administrado así como características relacionadas, como ejecutar, adjuntar, establecer punto de interrupción, editar y continuar y otros. Sin embargo, el motor de depuración no admite la depuración de base de datos de SQL Server.  
  
 Aunque admite la depuración nativa está incluida en el paquete básico del depurador, no se puede extender para admitir idiomas adicionales.  
  
#### <a name="3-source-code-control-integration"></a>3. Integración del Control de código fuente  
 El shell integrado proporciona las API para implementar el control de código fuente (SCC) y para proporcionar el control de código fuente común basada en MSSCCI componentes de integración.  
  
 Aunque la integración del control de código fuente no es una característica habitual de la edición Pro de Visual Studio, la integración de SCC se proporciona en el shell integrado.  
  
#### <a name="4-build-support"></a>4. Compatibilidad de compilación  
 El shell integrado proporciona compatibilidad con la compilación. Puede encontrar información sobre las compilaciones en la [MSBuild Reference](../msbuild/msbuild-reference.md).  
  
## <a name="features-not-included-in-the-integrated-shell"></a>Características no incluidas en el Shell integrado  
 La siguiente es una lista de características que no están incluidos en el shell integrado:  
  
-   Diseñador de clases  
  
-   [Protección de preEmptive - Dotfuscator](../ide/dotfuscator/index.md)  
  
-   Características del lenguaje  
  
-   VSHost  
  
-   Ningún idioma de Visual Studio o sus plantillas de proyecto asociado o plantillas de elemento de proyecto, se incluyen en el shell integrado. Implementaciones específicas del idioma de otras características no se incluyen para fragmentos de código de Visual Basic de ejemplo.  
  
## <a name="see-also"></a>Vea también  
 [Extender la información general de Visual Studio](../Topic/Extending%20Visual%20Studio%20Overview.md)
