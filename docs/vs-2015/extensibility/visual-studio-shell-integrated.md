---
title: Visual Studio Shell (integrado) | Microsoft Docs
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
ms.openlocfilehash: 907b71d82a3c630bedc48209e735d9cf817432ad
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "85543161"
---
# <a name="visual-studio-shell-integrated"></a>Visual Studio Shell (integrado)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

El shell integrado de Visual Studio incluye el entorno de desarrollo integrado (IDE), el depurador y la integración del control de código fuente. No se incluye ningún lenguaje de programación. Sin embargo, el shell integrado proporciona un marco que permite agregar lenguajes de programación.  
  
 El shell integrado de Visual Studio es realmente una combinación del shell aislado de Visual Studio más una instalación adicional que incluye componentes específicos de Shell integrados.  La aplicación de Shell integrada debe incluir tanto el paquete redistribuible de Shell aislado como el paquete redistribuible de Shell integrado, tanto de [Microsoft Visual Studio de paquetes redistribuibles de Shell](https://visualstudio.microsoft.com/vs/older-downloads/isolated-shell/).  
  
> [!NOTE]
> Antes de poder tener acceso a los paquetes redistribuibles de Shell, aislados e integrados, se le pedirá que rellene una breve encuesta de clientes.  Después de rellenar la encuesta, se le dirigirá a una página de Visual Studio Connect con vínculos de descarga de paquetes redistribuibles.  Puede encontrar los vínculos de descarga en las visitas posteriores al sitio de Visual Studio Connect en la pestaña **programas &#124; el shell integrado y aislado de Visual studio 2015** .  
  
 Si instala la aplicación de Shell integrada en el mismo equipo que una versión completa de Visual Studio, los componentes de la aplicación se integrarán directamente en Visual Studio.  
  
## <a name="features-in-the-integrated-shell"></a>Características del shell integrado  
  
|Área de características|Característica|  
|-|-|  
|Compatibilidad con idiomas|-Ninguno|  
|IDE|<ul><li>Configuración<br /><br /> <ul><li>Crear configuración</li><li>Importar y exportar configuraciones</li><li>Restablecer la configuración</li></ul></li><li>Integración del **cuadro de herramientas**</li><li>Integración de **lista de tareas**</li><li>Integración de la ayuda</li><li>Cuadro de diálogo **Opciones**</li><li>Administración de fuentes y colores</li><li>Ventana de **salida**</li><li>Ventana **comandos**</li><li>Administración de ventanas</li><li>Comandos, menús y enlaces de teclado</li><li>Tiempo de ejecución de lenguaje específico de dominio (DSL)</li></ul>|  
|Tipos de proyecto y sistema de proyectos|-Soluciones y carpetas de soluciones<br />-Administrador de configuración de soluciones<br />-Administración de elementos<br />-Soluciones de proyecto único y de varios proyectos<br />-Diseñador de aplicaciones (propiedades de proyecto simplificadas)<br />-Agregar referencia Web<br />-Agregar referencia de servicio<br />-Proyecto único<br />-Tipos de proyecto de sitio web<br />-Proyectos de aplicación Web|  
|Compilar|-Pasos de compilación personalizada en IDE<br />-Precompilación para la protección de propiedad intelectual (IP)<br />-Firma de código<br />     MSBuild|  
|Editor|-Herramientas de exploración de código (búsqueda unificada, definición de origen, herencia)<br />-Navegación de código<br />-IntelliSense<br />-SmartTags<br />-Refactorización<br />-Listado con sangría<br />-Filtrado de IntelliSense<br />-   Ventana **definición de código**|  
|Diseñador|-Windows Presentation Foundation diseñador<br />-Diseñador de Windows Forms<br />-Diseñador Web y editor HTML|  
|data|-   **Explorador de servidores** (simplificado: solo datos). Vea la Nota 1.<br />-   Ventana **orígenes de datos**<br />-Conjunto completo de controles de datos<br />-Editor XML<br />: Enlace de datos al origen de datos local (. MDF o. MDB<br />-Enlazar datos a objeto<br />: Enlace de datos al servicio Web<br />-Enlazar datos a servidor de base de datos local<br />-Enlazar datos al servidor de base de datos remoto<br />-Herramientas de DDL para datos remotos<br />-   Extensibilidad de **Explorador de servidores** ( [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] ejemplos)|  
|instantáneas|-Depuración local. Vea la nota 2.<br />-Depuración administrada<br />-Depuración local<br />-Asociar al proceso local<br />-Asociar al proceso remoto<br />-Delegado anónimo<br />-Dominios de aplicación<br />-Depuración de ASPX<br />-Atributos<br />-Break durante la evaluación de FUNC<br />-Puntos de interrupción<br />-Restricciones de punto de interrupción<br />-CallStack<br />-   Ventana **comandos**<br />-Depuración entre subprocesos<br />-Sugerencias de datos<br />-Visualizador de datos<br />-Compatibilidad del depurador con asistentes para la depuración administrada (MDA)<br />-Compatibilidad del depurador con el reenviador de tipos<br />: Compatibilidad de DTEEvents con OTB<br />-El stepper de JMC<br />-Prueba AppID del depurador (DBGCLR)<br />-Perfil del depurador<br />-Herramientas y opciones del depurador<br />-Iterador de depuración<br />-Evaluación de expresiones en tiempo de diseño<br />-Evaluador de expresiones de C#<br />-Desensamblado<br />-Editar y continuar<br />-Ventanas del evaluador de expresiones (inspección, variables locales, automático)<br />-Aplicación auxiliar de excepciones<br />-Excepciones<br />-Ejecución<br />- Genéricos<br />-Obteniendo el origen derecho<br />-Depuración HPC/Cluster<br />-Depuración integrada en varios idiomas<br />-Depuración de interoperabilidad<br />-Depuración Just-in-Time<br />-Depuración local<br />-Depuración administrada<br />-Control manual (ventana procesos)<br />- Memoria<br />-Compatibilidad con minivolcado<br />-Módulos<br />-Depuración de varios procesos<br />-Depuración nativa<br />-Nueva compatibilidad con el motor de depuración<br />-Depuración de código optimizado<br />-Filtrado de Windows de salida<br />-Hospedaje de procesos para la depuración administrada<br />-Procesos<br />-Inspección rápida<br />-Registros<br />-Registros en la pila<br />-Depuración remota<br />-Valores devueltos<br />-Depuración de scripts<br />-Compatibilidad con el servicio de origen<br />-Seguridad<br />-En paralelo<br />-SQL<br />-Servidor de símbolos<br />-Puntos de seguimiento<br />-Subproceso<br />-Visualizaciones<br />-Depurador de transformaciones del lenguaje de hojas de estilo extensible (XSLT)|  
|Compatibilidad con 64 bits|-depuración de 64 bits para código administrado y nativo, todos los lenguajes<br />-compatibilidad nativa con x64|  
|Control de código fuente (SCC)|-Integración básica de SCC. Vea la Nota 3.<br />-Comprobación de herramientas y opciones|  
|Extensibilidad|-Consumo de componentes VSPackages y MEF|  
  
## <a name="notes"></a>Notas  
  
#### <a name="1-data-tools"></a>1. herramientas de datos  
 El shell integrado incluye herramientas de desarrollo de bases de datos, como la compatibilidad con la extensibilidad de datos y el **Explorador de soluciones**simplificado. Sin embargo, los informes de SQL Server Express, SQL Reporting y Crystal no se incluyen en el shell integrado.  
  
#### <a name="2-debugging-support"></a>2. compatibilidad con la depuración  
 El shell integrado incluye el mismo motor de depuración que se incluye en la versión Community de Visual Studio. El motor de depuración incluye el depurador común para código administrado y también características relacionadas, como ejecutar, adjuntar, establecer punto de interrupción, editar y continuar, etc. Sin embargo, el motor de depuración no admite SQL Server la depuración de bases de datos.  
  
 Aunque la compatibilidad con la depuración nativa está incluida en el paquete del depurador básico, no se puede ampliar para admitir otros idiomas.  
  
#### <a name="3-source-code-control-integration"></a>3. integración del control de código fuente  
 El shell integrado proporciona las API para implementar el control de código fuente (SCC) y proporcionar los componentes de integración de control de código fuente comunes basados en MSSCCI.  
  
 Aunque la integración de SCC no es una característica normal de la edición pro de Visual Studio, la integración de SCC se proporciona en el shell integrado.  
  
#### <a name="4-build-support"></a>4. compatibilidad con la compilación  
 El shell integrado proporciona compatibilidad con la compilación. Puede encontrar información sobre las compilaciones en la [referencia de MSBuild](../msbuild/msbuild-reference.md).  
  
## <a name="features-not-included-in-the-integrated-shell"></a>Características no incluidas en el shell integrado  
 A continuación se muestra una lista de las características que no se incluyen en el shell integrado:  
  
- Diseñador de clases  
  
- PreEmptive Protection - Dotfuscator  
  
- Características del lenguaje  
  
- VSHost  
  
- No se incluyen en el shell integrado ningún lenguaje de Visual Studio ni sus plantillas de proyecto o plantillas de elemento de proyecto asociadas. No se incluyen implementaciones específicas del lenguaje de otras características, por ejemplo Visual Basic fragmentos de código.  
  
## <a name="see-also"></a>Consulte también  
 [Información general sobre la extensión de Visual Studio](https://msdn.microsoft.com/library/3e9078d7-2763-4cc4-8e20-fac69d747f59)
