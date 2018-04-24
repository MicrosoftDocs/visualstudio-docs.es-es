---
title: Elegir una estrategia de actualización de ClickOnce | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- application updates, ClickOnce
- updates, ClickOnce
- ClickOnce deployment, update strategies
ms.assetid: d8b6e7bb-4ea0-47f3-91cd-48580bdceccc
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0013b9f7ae004b709a1651af0e32e36dd45f909c
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/19/2018
---
# <a name="choosing-a-clickonce-update-strategy"></a>Elegir una estrategia de actualización de ClickOnce
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] puede proporcionar actualizaciones automáticas de aplicaciones. Un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicación lee periódicamente su archivo de manifiesto de implementación para ver si hay disponibles actualizaciones a la aplicación. En caso afirmativo, la nueva versión de la aplicación se descarga y se ejecuta. Para una mayor eficiencia, se descargan sólo los archivos que han cambiado.  
  
 A la hora de diseñar una aplicación [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], es necesario determinar qué estrategia utilizará la aplicación para comprobar si hay actualizaciones disponibles. Se pueden utilizar tres estrategias básicas: comprobar si hay actualizaciones al inicio de la aplicación, comprobar si hay actualizaciones después del inicio de la aplicación (ejecutándose en un subproceso de segundo plano) o proporcionando una interfaz de usuario para las actualizaciones.  
  
 Además, puede determinar con qué frecuencia debe comprobar la aplicación si hay actualizaciones y puede hacer que las actualizaciones sean obligatorias.  
  
> [!NOTE]
>  Las actualizaciones de aplicaciones requieren conectividad de red. Si no hay conexión de red, la aplicación se ejecutará sin comprobar si hay actualizaciones, independientemente de la estrategia de actualización elegida.  
  
> [!NOTE]
>  En .NET Framework 2.0 y .NET Framework 3.0, cada vez que la aplicación comprueba si hay actualizaciones, antes o después del inicio, o mediante las API de <xref:System.Deployment.Application>, debe establecer `deploymentProvider` en el manifiesto de implementación. El `deploymentProvider` elemento corresponde en Visual Studio para la **Actualizar ubicación** campo el **actualizaciones** cuadro de diálogo de la **publicar** ficha. Esta regla es más flexible en .NET Framework 3.5. Para obtener más información, consulte [implementación ClickOnce aplicaciones para las pruebas y los servidores de producción sin Resigning](../deployment/deploying-clickonce-applications-for-testing-and-production-servers-without-resigning.md).  
  
## <a name="checking-for-updates-after-application-startup"></a>Comprobar si hay actualizaciones después del inicio de la aplicación  
 Con esta estrategia, la aplicación intentará buscar y leer en segundo plano el archivo de manifiesto de implementación mientras la aplicación se está ejecutando. Si hay una actualización disponible, la próxima vez que el usuario ejecute la aplicación, se le pedirá que descargue e instale la actualización.  
  
 Esta estrategia funciona mejor para las conexiones de red con un bajo ancho de banda o para las aplicaciones de gran tamaño que podrían requerir mucho tiempo de descarga.  
  
 Para habilitar esta estrategia de actualización, haga clic en **tras iniciar la aplicación** en el **Elija cuándo debe buscar actualizaciones la aplicación** sección de la **actualizaciones de la aplicación** cuadro de diálogo. A continuación, especifique un intervalo de actualización en la sección **especificar la frecuencia con la que la aplicación buscará actualizaciones**.  
  
 Esto es lo mismo que cambiar la **actualización** elemento de la implementación del manifiesto como sigue:  
  
```  
<!-- When to check for updates -->  
<subscription>  
   <update>  
      <expiration maximumAge="6" unit="hours" />  
   </update>  
</subscription>  
```  
  
## <a name="checking-for-updates-before-application-startup"></a>Comprobar si hay actualizaciones antes del inicio de la aplicación  
 La estrategia predeterminada consiste en intentar buscar y leer el archivo de manifiesto de implementación antes de que se inicie la aplicación. Con esta estrategia, la aplicación intentará buscar y leer el archivo de manifiesto de implementación cada vez que el usuario inicie la aplicación. Si hay disponible alguna actualización, se descargará y se iniciará; de lo contrario, se iniciará la versión existente de la aplicación.  
  
 Esta estrategia funciona mejor para las conexiones de red de un ancho de banda elevado; el retraso en el inicio de la aplicación puede ser inaceptablemente largo en conexiones de ancho de banda reducido.  
  
 Para habilitar esta estrategia de actualización, haga clic en **antes de iniciar la aplicación** en el **Elija cuándo debe buscar actualizaciones la aplicación** sección de la **actualizaciones de la aplicación** cuadro de diálogo.  
  
 Esto es lo mismo que cambiar la **actualización** elemento de la implementación del manifiesto como sigue:  
  
```  
<!-- When to check for updates -->  
<subscription>  
   <update>  
      <beforeApplicationStartup />  
   </update>  
</subscription>  
```  
  
## <a name="making-updates-required"></a>Hacer que las actualizaciones sean obligatorias  
 Puede haber ocasiones en las que desea obligar a los usuarios a ejecutar una versión actualizada de su aplicación. Por ejemplo, podría realizar un cambio en un recurso externo como un servicio Web que impediría que funcionara correctamente la versión anterior de su aplicación. En este caso, debería marcar su actualización como obligatoria e impedir que los usuarios ejecuten la versión anterior.  
  
> [!NOTE]
>  Aunque puede requerir actualizaciones utilizando las otras estrategias de actualización, comprobar su existencia **antes de iniciar la aplicación** es la única manera de garantizar que no se puede ejecutar una versión anterior. Si la actualización obligatoria se detecta al inicio, el usuario deberá aceptarla o cerrar la aplicación.  
  
 Para marcar una actualización si es necesario, haga clic en **especificar la versión mínima requerida para esta aplicación** en el **aplicación actualiza** diálogo cuadro y, a continuación, especifique la versión de publicación (**principales**, **Secundaria**, **generar**, **revisión**), que especifica el número de versión más bajo de la aplicación que se pueden instalar.  
  
 Esto es lo mismo que establecer el **minimumRequiredVersion** atributo de la **implementación** elemento en el manifiesto de implementación; por ejemplo:  
  
```  
<deployment install="true" minimumRequiredVersion="1.0.0.0">  
```  
  
## <a name="specifying-update-intervals"></a>Especificar intervalos de actualización  
 También puede especificar con qué frecuencia se comprueba si hay actualizaciones. Para ello, especifique que la aplicación debe comprobar si hay actualizaciones tras el inicio, tal y como se ha descrito anteriormente en la sección "Comprobar si hay actualizaciones tras el inicio de la aplicación".  
  
 Para especificar el intervalo de actualización, establezca la **especificar la frecuencia con la que la aplicación buscará actualizaciones** propiedades en el **actualizaciones de la aplicación** cuadro de diálogo.  
  
 Esto es lo mismo que establecer el **maximumAge** y **unidad** atributos de la **actualización** elemento en el manifiesto de implementación.  
  
 Por ejemplo, puede desear comprobarlo cada vez que se ejecuta la aplicación, o una vez por semana o una vez al mes. Si no hay ninguna conexión de red en el momento especificado, la comprobación de actualización se realizará la próxima vez que se ejecute la aplicación.  
  
## <a name="providing-a-user-interface-for-updates"></a>Proporcionar una interfaz de usuario para las actualizaciones  
 Con esta estrategia, el desarrollador de la aplicación proporciona una interfaz que permite al usuario elegir cuándo y con qué frecuencia comprobará la aplicación si hay actualizaciones. Por ejemplo, podría proporcionar un elemento de menú "Comprobar ahora si hay actualizaciones" o un cuadro de diálogo "Configuración de actualizaciones" que ofrezca opciones para distintos intervalos de actualización. El [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] las API de implementación proporcionan un marco de trabajo para la programación de su propia interfaz de usuario de actualización. Para obtener más información, vea el espacio de nombres <xref:System.Deployment.Application>.  
  
 Si la aplicación utiliza las API de implementación para controlar su propia lógica de actualización, debería bloquear la comprobación de actualizaciones del modo en que se describe en la sección "Bloquear la comprobación de actualizaciones" que se muestra más adelante.  
  
 Esta estrategia es más adecuada cuando es necesario disponer de diferentes estrategias de actualización para los distintos usuarios.  
  
## <a name="blocking-update-checking"></a>Bloquear la comprobación de actualizaciones  
 También es posible impedir que su aplicación compruebe si hay actualizaciones disponibles. Por ejemplo, podría tener una aplicación sencilla que no se vaya a actualizar nunca, pero desea aprovechar la facilidad de instalación que ofrece la implementación de [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  
  
 Deberá bloquear también la comprobación de actualizaciones si la aplicación utiliza las API de implementación para realizar sus propias actualizaciones; vea la sección "Proporcionar una interfaz de usuario para las actualizaciones" anterior.  
  
 Para bloquear la comprobación de actualizaciones, desactive la **la aplicación buscará actualizaciones** casilla de verificación en el cuadro de diálogo de las actualizaciones de aplicación.  
  
 También puede bloquear la comprobación de actualizaciones quitando la etiqueta `<Subscription>` del manifiesto de implementación.  
  
## <a name="permission-elevation-and-updates"></a>Elevación de permisos y actualizaciones  
 Si una nueva versión de una aplicación [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] exige un mayor nivel de confianza para ejecutarse que en la versión anterior, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] preguntará al usuario si desea que se conceda a la aplicación este nivel de confianza superior. Si el usuario lo declina, la actualización no se instalará. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] preguntará al usuario si desea volver a instalar la aplicación la próxima vez que se reinicie. Si, en esta ocasión, el usuario vuelve a declinar que se conceda un mayor nivel de confianza y la actualización no está marcada como obligatoria, se ejecutará la versión anterior de la aplicación. Sin embargo, si la actualización es obligatoria, la aplicación no se ejecutará de nuevo hasta que el usuario acepte el nivel de confianza superior.  
  
 Si utiliza la implementación de aplicaciones de confianza, no se realizará ninguna pregunta sobre los niveles de confianza. Para obtener más información, consulta [Trusted Application Deployment Overview](../deployment/trusted-application-deployment-overview.md).  
  
## <a name="see-also"></a>Vea también  
 <xref:System.Deployment.Application>   
 [Seguridad e implementación ClickOnce](../deployment/clickonce-security-and-deployment.md)   
 [Elegir una estrategia de implementación de ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md)   
 [Proteger las aplicaciones ClickOnce](../deployment/securing-clickonce-applications.md)   
 [Cómo realiza ClickOnce actualizaciones de aplicaciones](../deployment/how-clickonce-performs-application-updates.md)   
 [Cómo: Administrar actualizaciones de aplicaciones ClickOnce](../deployment/how-to-manage-updates-for-a-clickonce-application.md)