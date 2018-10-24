---
title: Recopilación de datos de rendimiento de un sitio web | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vsperf.url.url
- vsperf.chooseurl
- vs.performance.wizard.asppage
- vsperf.url.ok
- vsperf.url.cancel
helpviewer_keywords:
- Profiling Tools,profiling ASP.NET
- web sites, performance profiling
- ASP.NET, performance profilng
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: bfe90b47086232650a38581bb2a8af1b534b8063
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49835993"
---
# <a name="how-to-collect-performance-data-for-a-web-site"></a>Recopilación de datos de rendimiento de un sitio web

Puede usar el **Asistente de rendimiento** para recopilar datos de rendimiento de una aplicación web de [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]. Puede generar perfiles de una aplicación web que esté abierta en Visual Studio o de un sitio web de [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] que se encuentre en el equipo local y que no esté abierto en el IDE de Visual Studio.

> [!NOTE]
> Con el **Asistente de rendimiento** puede agregar datos de generación de perfiles de interacción de capa (TIP), datos de rendimiento de JScript o ambos tipos de datos a los datos de generación de perfiles recopilados. La opción TIP recopila datos de los procesos del servidor. La generación de perfiles de JScript recopila datos de los scripts que se ejecutan en un sitio web local o remoto. En la mayoría de los casos, debe elegir solo una de las opciones.

 En función de la configuración de los permisos de acceso de usuario que haya facilitado un administrador, un usuario puede o no tener permiso de seguridad para crear una sesión del generador de perfiles en el equipo que hospeda el proceso de ASP.NET. En los siguientes ejemplos se muestran las posibles diferencias existentes entre los usuarios:

- Algunos usuarios podrían acceder a las características avanzadas de generación de perfiles cuando el administrador ha configurado el controlador y el servicio para que se inicien.

- Los usuarios de dominio podrían tener acceso solo a la generación de perfiles de ejemplo.

- Algunos usuarios podrían denegar el acceso a la generación de perfiles a todos los demás usuarios.

  Para obtener más información, vea [Generación de perfiles y seguridad de Windows Vista](../profiling/profiling-and-windows-vista-security.md) y las opciones de administración de [VSPerfCmd](../profiling/vsperfcmd.md).

## <a name="to-profile-a-web-site-project"></a>Para generar perfiles de un proyecto de sitio web

1. Abra el proyecto web [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] en Visual Studio.

2. En el menú **Analizar**, seleccione **Generador de perfiles de rendimiento**, **Explorador de rendimiento** e **Iniciar**.

3. En la primera página del asistente, seleccione un método de generación de perfiles y haga clic en **Siguiente**. Para obtener más información sobre los métodos de generación de perfiles, vea [Introducción a los métodos de generación de perfiles](../profiling/understanding-performance-collection-methods.md). Tenga en cuenta que el método de generación de perfiles del visualizador de simultaneidad no está disponible para las aplicaciones web.

4. En la lista desplegable **¿Para qué aplicación desea generar perfiles?** , asegúrese de que el proyecto actual está seleccionado y haga clic en **Siguiente**.

5. En la tercera página del asistente puede agregar datos de generación de perfiles de interacción de capa (TIP), datos del JavaScript que se ejecuta en las páginas web o ambos tipos de datos.

    - Para recopilar la interacción de capa, active la casilla **Habilitar generación de perfiles de interacción de capa** .

    - Para recopilar datos del JavaScript que se ejecuta en las páginas web, active la casilla **Generar perfiles de JavaScript** .

6. Haga clic en **Siguiente**.

7. En la cuarta página del asistente, haga clic en **Finalizar**.

8. Se creará una sesión de rendimiento para la aplicación de [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] y el sitio web se abrirá en el explorador. Ejecute la funcionalidad de la que quiere generar perfiles y, luego, cierre el explorador.

     El generador de perfiles genera el archivo de datos y muestra la vista de resumen de los datos en la ventana principal de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .

## <a name="to-profile-a-web-site-without-opening-a-project-in-visual-studio"></a>Para generar perfiles de un sitio web sin tener que abrir un proyecto en Visual Studio

1. Abra Visual Studio.

2. En el menú **Analizar**, seleccione **Generador de perfiles de rendimiento**, **Explorador de rendimiento** e **Iniciar**.

3. En la primera página del asistente, seleccione un método de generación de perfiles y haga clic en **Siguiente**. Para obtener más información, vea [Introducción a los métodos de generación de perfiles](../profiling/understanding-performance-collection-methods.md).

4. En la segunda página del asistente, seleccione la opción **Generar perfiles de una aplicación ASP.NET o JavaScript** y haga clic en **Siguiente**.

5. En el cuadro **¿Qué dirección URL o ruta de acceso ejecutará la aplicación web?** de la tercera página del asistente, escriba la dirección URL a la página de inicio de la aplicación y haga clic en **Siguiente**.

   - Para un sitio web basado en un servidor (IIS), escriba una dirección URL como **<http://localhost/MySite/default.aspx>**. Esto hace que se genere un perfil de la aplicación de [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] ubicada en la raíz de la aplicación de Mi sitio del equipo local y que el default.aspx de la página en ese sitio se inicie en Internet Explorer para iniciar la sesión.

   - Para un sitio web basado en un archivo, escriba una ruta de acceso como ///**c:\WebSites\MySite\default.aspx**. Esto hace que se genere un perfil de la aplicación de [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] ubicada en c:\webSites\MySite y que la página http://localhost:nnnn/MySite/default.aspx se inicie en Internet Explorer para iniciar la sesión.

   - Para los sitios externos en los que quiera recopilar datos de JavaScript, escriba la dirección URL (por ejemplo, http://www.contoso.com).

     Para obtener más información, consulte las páginas de propiedades de un binario de destino de [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] .

6. En la tercera página del asistente puede agregar datos de generación de perfiles de interacción de capa (TIP), datos del JavaScript que se ejecuta en las páginas web o ambos tipos de datos.

    - Para recopilar la interacción de capa, active la casilla **Habilitar generación de perfiles de interacción de capa** .

    - Para recopilar datos del JavaScript que se ejecuta en las páginas web, active la casilla **Generar perfiles de JavaScript**.

7. Haga clic en **Siguiente**.

8. En la cuarta página del asistente, haga clic en **Finalizar**.

9. Se creará una sesión de rendimiento para la aplicación ASP.NET y el sitio web se abrirá en el explorador. Ejecute la funcionalidad de la que quiere generar perfiles y, luego, cierre el explorador.

     El generador de perfiles genera el archivo de datos y muestra la vista de resumen de los datos en la ventana principal de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .

## <a name="see-also"></a>Vea también

[Información general](../profiling/overviews-performance-tools.md)  
[Configuración de sesiones de rendimiento](../profiling/configuring-performance-sessions.md)  
[Introducción a los valores de datos de instrumentación](../profiling/understanding-instrumentation-data-values.md)  
[Introducción a los valores de datos de muestreo](../profiling/understanding-sampling-data-values.md)
