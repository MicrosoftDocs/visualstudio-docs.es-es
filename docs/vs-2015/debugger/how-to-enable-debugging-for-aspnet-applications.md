---
title: 'Cómo: habilitar la depuración de aplicaciones de ASP.NET | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugging ASP.NET Web applications
- Web.config configuration file, debug mode
- debugging [Visual Studio], ASP.NET
ms.assetid: 3beed819-cece-4864-8184-bd410000973a
caps.latest.revision: 40
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b9d0e7a4b6f6daf4fb93884e6d5673ce550259ca
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49235942"
---
# <a name="how-to-enable-debugging-for-aspnet-applications"></a>Cómo: Habilitar la depuración de aplicaciones de ASP.NET
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Para habilitar la depuración, debe habilitarla en la página **Propiedades del proyecto** y en el archivo de configuración web.config de la aplicación.  
  
> [!NOTE]  
> Los cuadros de diálogo y comandos de menú que se ven pueden diferir de los descritos en la Ayuda, en función de los valores de configuración o de edición activos. Para cambiar la configuración, elija la opción **Importar y exportar configuraciones** del menú **Herramientas** . Para obtener más información, consulte [Personalizar la configuración de desarrollo en Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-enable-aspnet-debugging-in-the-project-properties-visual-basicc"></a>Para habilitar la depuración ASP.NET en las propiedades del proyecto (Visual Basic/C #)  
  
1.  En el **Explorador de soluciones**, haga clic con el botón secundario en el nombre de un proyecto web y seleccione **Propiedades**.  
  
2.  En la página de propiedades del proyecto, haga clic en la pestaña **Web** .  
  
3.  En **Depuradores**, active la casilla **ASP.NET** .  
  
### <a name="to-enable-debugging-in-the-webconfig-file"></a>Para habilitar la depuración en el archivo web.config  
  
1.  Abra el archivo web.config utilizando cualquier editor de texto estándar o un analizador XML.  
  
    > [!NOTE]  
    > Sin embargo, no se puede tener acceso al archivo en modo remoto utilizando un explorador web. Por motivos de seguridad, [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] configura Microsoft IIS para impedir el acceso directo del explorador a los archivos Web.config. Si intenta obtener acceso a un archivo de configuración utilizando un explorador, obtendrá el error de acceso 403 de HTTP (prohibido).  
  
2.  Web.config es un archivo XML, por lo que contiene secciones anidadas marcadas por etiquetas. Busque el elemento `configuration/system.web/compilation` . Si el elemento compilation no existe, créelo.  
  
3.  Si el elemento `compilation` no tiene un atributo `debug` , agregue el atributo al elemento.  
  
4.  Asegúrese de que el valor del atributo `debug` está establecido en `true`.  
  
El archivo web.config debe ser similar al del ejemplo siguiente. Tenga en cuenta que puede haber secciones entre los elementos configuration y system.web  
  
-   secciones element entre los elementos configuration y system.web  
  
-   secciones element entre los elementos system.web y compilation  
  
-   El elemento compilation puede contener otros atributos y elementos.  
  
## <a name="example"></a>Ejemplo  
  
```  
<configuration>  
    ...  
    <system.web>  
        <compilation  
            debug="true"  
            ...  
        >  
        ...  
        </compilation>  
    </system.web>  
</configuration>  
```  
  
## <a name="robust-programming"></a>Programación sólida  
[!INCLUDE[vstecasp](../includes/vstecasp-md.md)] detecta automáticamente los cambios realizados en los archivos Web.config y aplica la nueva configuración. No es preciso reiniciar el equipo ni el servidor IIS para que los cambios surtan efecto.  
  
Un sitio web puede contener varios directorios y subdirectorios virtuales, y pueden haber archivos Web.config en cada uno de ellos. Las aplicaciones [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] heredan los valores de los archivos Web.config ubicados en niveles superiores de la ruta de acceso de la dirección URL. Los archivos de configuración jerárquicos permiten cambiar la configuración de varias aplicaciones [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] simultáneamente, por ejemplo de todas las aplicaciones que se encuentren por debajo en la jerarquía. Sin embargo, si se establece el atributo `debug` en un archivo inferior en la jerarquía, reemplazará el valor más alto.  
  
De este modo, puede especificar `debug="true"` en www.microsoft.com/aaa/Web.config y todas las aplicaciones de la carpeta aaa y todas las subcarpetas de aaa heredarán esa configuración. Por tanto, si la aplicación [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] está en www.microsoft.com/aaa/bbb, heredará dicha configuración, al igual que cualquier aplicación [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] en www.microsoft.com/aaa/ccc, www.microsoft.com/aaa/ddd, etc. La única excepción es si una de esas aplicaciones reemplaza la configuración por medio de su propio archivo Web.config inferior.  
  
Si se habilita el modo de depuración, afectará enormemente al rendimiento de la aplicación [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] . No olvide deshabilitar el modo de depuración antes de implementar la aplicación o realizar controles de rendimiento.  
  
## <a name="see-also"></a>Vea también  
[Depurar aplicaciones de ASP.NET y AJAX](../debugger/debugging-aspnet-and-ajax-applications.md)  
  




