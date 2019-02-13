---
title: Localizar aplicaciones ClickOnce | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- WPF, ClickOnce applications
- ClickOnce deployment, globalization
- deploying applications [ClickOnce], localizing ClickOnce applications
- localization, ClickOnce deployment
- ClickOnce deployment, download on-demand
- ClickOnce deployment, localization
- Windows Forms, ClickOnce applications
- console applications, ClickOnce applications
ms.assetid: c92b193b-054d-4923-834b-d4226a4c7a1a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3c7ef2073afe7321bfee6d100e7df644bc9b3eed
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "55005220"
---
# <a name="localize-clickonce-applications"></a>Localización de aplicaciones ClickOnce
La localización es el proceso de adaptar una aplicación a una referencia cultural concreta. Este proceso implica traducir el texto de la interfaz de usuario a un idioma específico de la región, usar el formato correcto de fecha y moneda, ajustar el tamaño de los controles en un formulario y reflejar los controles de derecha a izquierda si es necesario.  
  
 Al localizar la aplicación, se crean uno o más ensamblados satélite. Cada ensamblado contiene cadenas de interfaz de usuario, imágenes y otros recursos específicos de una referencia cultural dada. (El archivo ejecutable principal de la aplicación contiene las cadenas de la referencia cultural predeterminada de la aplicación).  
  
 En este tema se describen tres maneras de implementar una aplicación de [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] para otras referencias culturales:  
  
-   Incluir todos los ensamblados satélite en una sola implementación.  
  
-   Generar una implementación para cada referencia cultural que incluya un único ensamblado satélite.  
  
-   Descargar ensamblados satélite a petición.  
  
## <a name="including-all-satellite-assemblies-in-a-deployment"></a>Incluir todos los ensamblados satélite en una implementación  
 En lugar de publicar varias implementaciones de [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], puede publicar una única implementación de [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] que contenga todos los ensamblados satélite.  
  
 Este es el método predeterminado en [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Para usar este método en [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], no es necesario realizar ningún trabajo adicional.  
  
 Para usar este método con *MageUI.exe*, establezca la referencia cultural de la aplicación en **neutro** en *MageUI.exe*. A continuación, incluya manualmente todos los ensamblados satélite en su implementación. En *MageUI.exe* puede agregar los ensamblados satélite mediante el botón **Rellenar** situado en la pestaña **Archivos** del manifiesto de su aplicación.  
  
 La ventaja de este enfoque es que crea una sola implementación y simplifica el proceso de implementación localizada. En tiempo de ejecución se usará el ensamblado satélite apropiado para la referencia cultural predeterminada del sistema operativo Windows del usuario. El inconveniente de este enfoque es que se descargan todos los ensamblados satélite cada vez que la aplicación se instala o actualiza en un equipo cliente. Si la aplicación tiene un gran número de cadenas o los clientes tienen una conexión de red lenta, este proceso puede afectar al rendimiento durante la actualización de la aplicación.  
  
> [!NOTE]
>  En este enfoque se presupone que la aplicación ajusta automáticamente el alto, el ancho y la posición de los controles para adaptarse a los diferentes tamaños de texto de las distintas referencias culturales. Windows Forms contiene diversos controles y tecnologías que le permiten diseñar el formulario de forma que se facilite la localización, incluidos los controles <xref:System.Windows.Forms.FlowLayoutPanel> y <xref:System.Windows.Forms.TableLayoutPanel> y la propiedad <xref:System.Windows.Forms.Control.AutoSize%2A>.  Consulte también [Cómo: Admitir la localización en formularios de Windows mediante AutoSize y el control TableLayoutPanel](/previous-versions/visualstudio/visual-studio-2010/1zkt8b33(v=vs.100)).  
  
## <a name="generate-one-deployment-for-each-culture"></a>Generar una implementación para cada referencia cultural  
 En esta estrategia de implementación se generan varias implementaciones. En cada una de ellas se incluye únicamente el ensamblado satélite necesario para una referencia cultural concreta y se marca la implementación como específica de esa referencia cultural.  
  
 Para usar este método en [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], establezca la propiedad **Idioma de publicación** de la pestaña **Publicar** en la región deseada. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] incluirá automáticamente el ensamblado satélite necesario para la región que seleccione y excluirá de la implementación los demás ensamblados satélite.  
  
 Puede conseguir lo mismo mediante la herramienta *MageUI.exe* de Microsoft [!INCLUDE[winsdklong](../deployment/includes/winsdklong_md.md)]. Use el botón **Rellenar** de la pestaña **Archivos** del manifiesto de aplicación para excluir todos los demás ensamblados satélite del directorio de la aplicación. Luego, establezca el campo **Referencia cultural** de la pestaña **Nombre** para el manifiesto de implementación en *MageUI.exe*. Estos pasos no solo incluyen el ensamblado satélite adecuado, sino que también establecen el atributo `language` en el elemento `assemblyIdentity` del manifiesto de su implementación en la referencia cultural correspondiente.  
  
 Después de publicar la aplicación, repita este paso con cada referencia cultural adicional que admita su aplicación. Asegúrese de que cada vez que publica, lo hace en un directorio de servidor web diferente o en un directorio de recurso compartido de archivos distinto, ya que cada manifiesto de aplicación hará referencia a un ensamblado satélite diferente y cada manifiesto de implementación tendrá un valor diferente para el atributo `language`.  
  
## <a name="download-satellite-assemblies-on-demand"></a>Descargar ensamblados satélite a petición  
 Si decide incluir todos los ensamblados satélite en una sola implementación, puede mejorar el rendimiento mediante la descarga a petición, que le permite marcar los ensamblados como opcionales. Los ensamblados marcados no se descargarán cuando se instala o actualiza la aplicación. Puede instalar los ensamblados cuando los necesite llamando al método <xref:System.Deployment.Application.ApplicationDeployment.DownloadFileGroup%2A> en la clase <xref:System.Deployment.Application.ApplicationDeployment>.  
  
 La descarga de ensamblados satélite a petición difiere ligeramente de la descarga de otros tipos de ensamblados a petición. Para obtener más información y ejemplos de código sobre cómo habilitar este escenario mediante la [!INCLUDE[winsdkshort](../debugger/debug-interface-access/includes/winsdkshort_md.md)] herramientas para [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], consulte [Tutorial: Descarga de ensamblados satélite a petición con la API de implementación de ClickOnce](../deployment/walkthrough-downloading-satellite-assemblies-on-demand-with-the-clickonce-deployment-api.md).  
  
 También puede habilitar este escenario en [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  Consulte también los tutoriales sobre [descarga de ensamblados satélite a petición con la API de implementación de ClickOnce mediante el diseñador](/previous-versions/visualstudio/visual-studio-2012/ms366788(v=vs.110)) o [descarga de ensamblados satélite a petición con la API de implementación de ClickOnce mediante el diseñador](/previous-versions/visualstudio/visual-studio-2013/ms366788(v=vs.120)).  
  
## <a name="testing-localized-clickonce-applications-before-deployment"></a>Prueba de aplicaciones ClickOnce localizadas antes de la implementación  
 Únicamente se usará un ensamblado para una aplicación de Windows Forms si la propiedad <xref:System.Threading.Thread.CurrentUICulture%2A> del subproceso principal de la aplicación está establecida en la referencia cultural del ensamblado satélite. Es probable que los clientes de los mercados locales ya tengan una versión localizada de Windows con su referencia cultural establecida en el valor predeterminado adecuado.  
  
 Tiene tres opciones para probar las implementaciones localizadas antes de poner la aplicación a disposición de los clientes:  
  
- Puede ejecutar su aplicación de [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] en las versiones localizadas apropiadas de Windows.  
  
- Puede establecer la propiedad <xref:System.Threading.Thread.CurrentUICulture%2A> mediante programación en la aplicación. (Esta propiedad debe establecerse antes de llamar al método <xref:System.Windows.Forms.Application.Run%2A>).  
  
## <a name="see-also"></a>Vea también  
 [\<assemblyIdentity > elemento](../deployment/assemblyidentity-element-clickonce-deployment.md)   
 [Seguridad e implementación ClickOnce](../deployment/clickonce-security-and-deployment.md)   
 [Globalizar formularios de Windows](/dotnet/framework/winforms/advanced/globalizing-windows-forms)