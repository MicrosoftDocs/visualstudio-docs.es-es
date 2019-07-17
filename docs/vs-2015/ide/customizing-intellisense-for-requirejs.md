---
title: Personalizar IntelliSense para RequireJS | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: 2be07ef8-9c08-444b-a21a-22a4fe6386a3
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: ce0aadf455e95895309bbae4f23eb84c75935428
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "68201873"
---
# <a name="customizing-intellisense-for-requirejs"></a>Personalizar IntelliSense para RequireJS
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A partir de su versión Update 4, Visual Studio 2013 es compatible con RequireJS, el popular cargador de módulos y archivos JavaScript. RequireJS facilita la definición de dependencias entre módulos de código y carga los módulos dinámicamente, solo cuando es necesario. Al escribir código JavaScript que use RequireJS, se ofrecerán sugerencias IntelliSense para los módulos a los que se haya hecho referencia desde la definición del módulo o mediante llamadas a `require()` desde dentro del código.  
  
 De forma predeterminada, Visual Studio incluye una configuración muy básica que permite utilizar RequireJS, aunque es habitual realizar una configuración personalizada (es decir, definir alias para las bibliotecas). Este tema describe las distintas maneras en que puede personalizar Visual Studio para trabajar con la configuración única de su proyecto.  
  
 En este tema se describe cómo:  
  
- Personalizar RequireJS en proyectos ASP.NET  
  
- Personalizar RequireJS en proyectos de JSProj, que se usan para crear aplicaciones de Apache Cordova y la Tienda Windows, y aplicaciones HTML de LightSwitch  
  
## <a name="customize-requirejs-in-aspnet-projects"></a>Personalizar RequireJS en proyectos ASP.NET  
 La compatibilidad con RequireJS se habilita de forma automática cuando un archivo JavaScript hace referencia a un archivo denominado require.js (para más información, vea la sección Determinar el contexto de IntelliSense en [IntelliSense para JavaScript](../ide/javascript-intellisense.md)). En los proyectos ASP.NET, las referencias a require.js suelen realizarse mediante una directiva /// \<reference/> dentro de un archivo _references.js.  
  
### <a name="configure-the-data-main-attribute-in-an-aspnet-project"></a>Configurar el atributo data-main en un proyecto de ASP.NET  
 Para simular con precisión el funcionamiento de la aplicación al ejecutarse, el editor de JavaScript necesita saber qué archivo debe cargar primero al configurar require.js. Esto normalmente se configura en el archivo HTML de la aplicación mediante el atributo `data-main` del elemento de script que hace referencia a require.js, como se muestra aquí.  
  
```html  
<script src="js/require.js" data-main="js/app.js"></script>  
```  
  
 En este ejemplo, el script al que hace referencia data-main (js/app.js) se carga inmediatamente después de require.js. El archivo que se carga inmediatamente es el mejor lugar para configurar el uso de RequireJS (mediante `require.config()`). Para indicar al editor de JavaScript qué archivo debe usar para `data-main` en la aplicación, agregue un atributo `data-main` y modifique una directiva /// \<reference/> que haga referencia a require.js en la aplicación. Por ejemplo, puede utilizar esta directiva:  
  
```javascript  
/// <reference path="js/require.js" data-main="js/app.js" />  
```  
  
### <a name="configure-the-application-start-page-in-an-aspnet-project"></a>Configurar la página de inicio de la aplicación en un proyecto de ASP.NET  
 Cuando se ejecuta la aplicación, RequireJS da por supuesto que relativa rutas de acceso a archivos (por ejemplo, ".. \\"rutas de acceso) son relativas al archivo HTML que cargó la biblioteca de require.js. Al escribir código en el editor de Visual Studio para un proyecto de ASP.NET, tenga en cuenta que esta página de inicio es desconocida y debe indicarle al editor qué página de inicio utilizar al emplear rutas de archivo relativas. Para ello, agregue un atributo `start-page` a la directiva /// \<reference/>.  
  
```javascript  
/// <reference path="js/require.js" data-main="js/app.js" start-page="/app/index.html" />  
```  
  
 El atributo `start-page` especifica la dirección URL de la página, tal como se vería en un explorador al ejecutarse la aplicación.  
  
## <a name="customize-requirejs-in-jsproj-projects"></a>Personalizar RequireJS en proyectos de JSProj  
 Los proyectos de JSProj (archivos de proyecto con la extensión .jsproj) se usan para crear aplicaciones para Apache Cordova, aplicaciones basadas en HTML para la Tienda Windows, o aplicación HTML de LightSwitch. A diferencia de los proyectos ASP.NET, estos leen las referencias a archivos .js de los archivos HTML existentes en el proyecto. Por este motivo, al editar JavaScript en un proyecto JSProj verá que la compatibilidad con RequireJS se habilita si se hace referencia al archivo JavaScript en edición en otro archivo HTML que también hace referencia a require.js.  
  
 Los pasos de personalización necesarios para los proyectos ASP.NET no hacen falta en un archivo de proyecto JSProj. Es decir, los archivos de script usados por el atributo `data-main` en la etiqueta de script que hace referencia a require.js se cargan automáticamente para configurar require.js. El archivo HTML que hace referencia a require.js también se utiliza como página de inicio de la aplicación.  
  
## <a name="see-also"></a>Vea también  
 [IntelliSense para JavaScript](../ide/javascript-intellisense.md)
