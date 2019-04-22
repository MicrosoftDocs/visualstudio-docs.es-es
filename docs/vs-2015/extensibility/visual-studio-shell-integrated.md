---
title: Visual Studio Shell (integrado) | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio shell, integrated mode features
- Shell [Visual Studio], integrated mode features
ms.assetid: 0b40d495-f17f-4bb9-ace8-b365a7172784
caps.latest.revision: 26
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 87c7b4faaf5aad737c8f7f8b653dbea03bc4de31
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "59003148"
---
# <a name="visual-studio-shell-integrated"></a>Visual Studio Shell (integrado)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

El shell integrado de Visual Studio incluye el entorno de desarrollo integrado (IDE), el depurador y la integración de control de código fuente. No se incluye ningún lenguaje de programación. Sin embargo, el shell integrado proporcionan un marco que le permite agregar lenguajes de programación.  
  
 El shell integrado de Visual Studio es realmente una combinación de la shell aislado de Visual Studio más de una instalación adicional que incluir componentes específicos de shell integrado.  La aplicación de shell integrado debe incluir tanto el shell aislado paquete redistribuible de [paquete redistribuible de Microsoft Visual Studio Shell (aislado)](http://go.microsoft.com/fwlink/?LinkId=616022) , así como el paquete redistribuible de shell integrado desde [Microsoft Visual Studio Shell (integrado) paquete redistribuible](http://go.microsoft.com/fwlink/?LinkId=616021).  
  
> [!NOTE]
>  Antes de que puede tener acceso a los paquetes redistribuibles del shell integrado y aislado, se le pedirá que rellene una breve encuesta de cliente.  Después de completar la encuesta, se le dirigirá a una página de Visual Studio Connect con vínculos de descarga del paquete redistribuible.  Puede encontrar los vínculos de descarga en visitas posteriores al sitio de Visual Studio Connect en el **programas &#124; VISUAL STUDIO 2015 integrado y aislado SHELL** ficha.  
  
 Si instala la aplicación de shell integrado en el mismo equipo que una versión completa de Visual Studio, componentes de la aplicación se integrarán directamente en Visual Studio.  
  
## <a name="features-in-the-integrated-shell"></a>Características en el Shell integrado  
  
|||  
|-|-|  
|Área de características|Característica|  
|Compatibilidad con lenguajes|-None|  
|IDE|<ul><li>Configuración<br /><br /> <ul><li>Crear una configuración</li><li>Importar y exportar configuraciones</li><li>Restablecer la configuración</li></ul></li><li>**Cuadro de herramientas** integración</li><li>**Lista de tareas** integración</li><li>Integración de la Ayuda</li><li>**Opciones de** cuadro de diálogo</li><li>Administración de fuentes y colores</li><li>**Salida** ventana</li><li>**Comando** ventana</li><li>Administración de ventanas</li><li>Los enlaces de teclado, menús y comandos</li><li>En tiempo de ejecución de lenguaje específico de dominio (DSL)</li></ul>|  
|Sistema de proyectos y tipos de proyecto|-Soluciones y las carpetas de soluciones<br />: Administrador de configuración de la solución<br />: Administración de elementos<br />-Proyecto único y varios proyectos de soluciones<br />-Diseñador de aplicaciones (propiedades del proyecto simplificada)<br />-Agregar referencia Web<br />-Agregar referencia de servicio<br />Proyecto único<br />: Tipos de proyecto de sitio Web de<br />: Proyectos de aplicación web|  
|Compilar|-Pasos de compilación personalizada en el IDE<br />-Precompilación para protección de la propiedad intelectual (IP)<br />: Firma de código<br />     MSBuild|  
|Editor|-(Búsqueda unificada, definición de origen, herencia) de herramientas de exploración de código<br />: Navegación de código<br />-   IntelliSense<br />-   SmartTags<br />-Refactorización<br />-Lista descriptiva<br />: Filtrado de IntelliSense<br />-   **Definición de código** ventana|  
|Diseñador|-Diseñador Windows Presentation Foundation<br />-Diseñador de formularios de Windows<br />-Editor de HTML y diseñador web|  
|Datos|-   **Explorador de servidores** (simplificado: sólo los datos). Vea la Nota 1.<br />-   **Orígenes de datos** ventana<br />-Todo el conjunto de controles de datos<br />-XML Editor<br />-Data enlaza al origen de datos local (. MDF o. MDB)<br />: Enlace de datos objeto<br />-Enlazar datos al servicio Web<br />-Data enlaza al servidor de base de datos local<br />-Data enlaza al servidor de base de datos remota<br />-Herramientas DDL para los datos remotos<br />-   **Explorador de servidores** extensibilidad ([!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] ejemplos)|  
|instantáneas|-Depuración local. Vea la nota 2.<br />-Depuración administrada<br />-Depuración local<br />-Adjuntar al proceso local<br />-Adjuntar al proceso remoto<br />-Delegado anónimo<br />: Dominios de aplicación<br />-Depuración ASPX<br />-Attributes<br />-Interrumpir durante la función eval<br />: Los puntos de interrupción<br />: Restricciones de punto de interrupción<br />: Pila de llamadas<br />-   **Comando** ventana<br />-Depuración entre subprocesos<br />: Sugerencias de datos<br />: Visualizador de datos<br />-Compatibilidad del depurador con asistentes para la depuración administradas (MDA)<br />-Compatibilidad con el depurador reenviador de tipos<br />-Compatibilidad con DTEEvents OTB<br />-JMC motor paso a paso<br />-Prueba de AppID debugger (DBGCLR)<br />: Perfil del depurador<br />-Herramientas y opciones del depurador<br />-Iteradores de depuración<br />-Evaluación de expresiones tiempo de diseño<br />-El evaluador de expresiones C#<br />-Desensamblado<br />-Editar y continuar<br />-Ventanas de evaluador de expresiones (inspección, variables locales, automático)<br />: Aplicación auxiliar de excepciones<br />: Excepciones<br />: Ejecución<br />- Genéricos<br />-Obtener el código fuente correcto<br />-Depuración de clúster HPC y de<br />-Depuración de varios idiomas integrada<br />-Depuración interoperabilidad<br />-Depuración just-in-time<br />-Depuración local<br />-Depuración administrada<br />-Control manual (ventana de procesos)<br />-Memoria<br />-Compatibilidad con minivolcado<br />-Modules<br />-Depuración de varios procesos<br />-Depuración nativa<br />-Nueva compatibilidad del motor de depuración<br />-Depuración de código optimizado<br />-Filtrado de windows output<br />-Proceso de hospedaje para la depuración administrada<br />-Procesos<br />-Inspección rápida<br />: Registra<br />-Registros de pila<br />-Depuración remota<br />: Valores devueltos de<br />: Depuración de scripts<br />-Compatibilidad con el servicio origen<br />-Seguridad<br />Side-by-side<br />-SQL<br />: Servidor de símbolos<br />: Puntos de seguimiento<br />: Subprocesos<br />-Visualizaciones<br />-Depurador de extensible Stylesheet Language Transformations (XSLT)|  
|compatibilidad con 64 bits|-depuración de 64 bits para código administrado y nativo, todos los idiomas<br />-admite x64 nativo|  
|Control de código fuente (SCC)|-Integración de SCC básica. Vea la Nota 3.<br />-Las herramientas y opciones de comprobación|  
|Extensibilidad|-Consumir los componentes MEF y VSPackages|  
  
## <a name="notes"></a>Notas  
  
#### <a name="1-data-tools"></a>1. Herramientas de datos  
 El shell integrado incluye herramientas de desarrollo de base de datos como la compatibilidad de extensibilidad de datos y la simplificada **el Explorador de soluciones**. Sin embargo, SQL Server Express, SQL Reporting y Crystal Reports no se incluyen en el shell integrado.  
  
#### <a name="2-debugging-support"></a>2. Capacidad de depuración  
 El shell integrado incluye el mismo motor de depuración que se incluye en la versión de comunidad de Visual Studio. El motor de depuración incluye al depurador para código administrado así como las características relacionadas, comunes, como ejecutar, adjuntar, establecer punto de interrupción, editar y continuar y otros. Sin embargo, el motor de depuración no admite la depuración de base de datos de SQL Server.  
  
 Aunque admite la depuración nativa está incluida en el paquete básico de depurador, no se puede extender para admitir idiomas adicionales.  
  
#### <a name="3-source-code-control-integration"></a>3. Integración del Control de código fuente  
 El shell integrado proporciona API para implementar el control de código fuente (SCC) y para proporcionar el control de código fuente comunes en función de MSSCCI componentes de integración.  
  
 Aunque la integración de SCC no es una característica habitual de la edición Pro de Visual Studio, se proporciona integración de SCC en el shell integrado.  
  
#### <a name="4-build-support"></a>4. Compatibilidad de compilación  
 El shell integrado proporciona compatibilidad con la compilación. Puede encontrar información sobre las compilaciones en el [referencia de MSBuild](../msbuild/msbuild-reference.md).  
  
## <a name="features-not-included-in-the-integrated-shell"></a>Características no incluidas en el Shell integrado  
 La siguiente es una lista de características que no están incluidos en el shell integrado:  
  
-   Diseñador de clases  
  
-   PreEmptive Protection - Dotfuscator  
  
-   Características del lenguaje  
  
-   VSHost  
  
-   Ningún idioma de Visual Studio o sus plantillas de proyecto asociado o plantillas de elemento de proyecto, se incluyen en el shell integrado. Implementaciones específicas de idioma de otras características no se incluyen, para fragmentos de código de Visual Basic de ejemplo.  
  
## <a name="see-also"></a>Vea también  
 [Ampliación de introducción a Visual Studio](http://msdn.microsoft.com/library/3e9078d7-2763-4cc4-8e20-fac69d747f59)