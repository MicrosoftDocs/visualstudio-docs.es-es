---
title: "&lt;dependency&gt; (Elemento) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "urn:schemas-microsoft-com:asm.v2#subscription"
  - "urn:schemas-microsoft-com:asm.v2#beforeApplicationStartup"
  - "urn:schemas-microsoft-com:asm.v2#deploymentProvider"
  - "urn:schemas-microsoft-com:asm.v2#update"
  - "urn:schemas-microsoft-com:asm.v2#deployment"
  - "urn:schemas-microsoft-com:asm.v2#expiration"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "<deployment> (elemento) [manifiesto de implementación ClickOnce]"
ms.assetid: 4fafa9c2-97a0-4cea-b8fd-9746dca33af4
caps.latest.revision: 30
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 30
---
# &lt;dependency&gt; (Elemento)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Identifica los atributos utilizados para la implementación de actualizaciones y exposición del sistema.  
  
## Sintaxis  
  
```  
  
      <deployment   
   install  
   minimumRequiredVersion  
   mapFileExtensions  
   disallowUrlActivation  
   trustUrlParameters  
>   
   <subscription>   
         <update>   
            <beforeApplicationStartup/>   
            <expiration  
               maximumAge  
               unit  
            />  
         </update>    
   </subscription>   
   <deploymentProvider   
      codebase   
   />   
</deployment>  
```  
  
## Elementos y atributos  
 Se requiere el elemento `deployment`, que se encuentra en el espacio de nombres `urn:schemas-microsoft-com:asm.v1`.  El elemento tiene los atributos siguientes.  
  
|Atributo|Descripción|  
|--------------|-----------------|  
|`install`|Obligatorio.  Especifica si dicha aplicación define una presencia en el menú **Inicio** de Windows y en la aplicación **Agregar o quitar programas** del Panel de control.  Los valores válidos son `true` y `false`.  Si es `false`, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] ejecutará siempre la última versión de esta aplicación desde la red y no reconocerá el elemento `subscription`.|  
|`minimumRequiredVersion`|Opcional.  Especifica la versión mínima de esta aplicación que se puede ejecutar en el cliente.  Si el número de versión de la aplicación es inferior al número de versión proporcionado en el manifiesto de implementación, la aplicación no se ejecutará.  Los números de versión deben especificarse en el formato `N.N.N.N`, donde `N` es un entero sin signo.  Si el atributo `install` es `false`, no se debe establecer `minimumRequiredVersion`.|  
|`mapFileExtensions`|Opcional.  El valor predeterminado es `false`.  Si es `true`, todos los archivos de la implementación deben tener la extensión .deploy.  [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] quitará esta extensión de estos archivos en cuanto los descargue del servidor web.  Si publica una aplicación mediante [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], esta extensión se agregará automáticamente a todos los archivos.  Este parámetro permite que todos los archivos de una implementación de [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] se descarguen desde un servidor web que bloquea la transmisión de los archivos que finalizan con extensiones "no seguras", como .exe.|  
|`disallowUrlActivation`|Opcional.  El valor predeterminado es `false`.  Si es `true`, impide que una aplicación instalada se inicie al hacer clic en la dirección URL o escribir la dirección URL en Internet Explorer.  Si el atributo `install` no está presente, se omite.|  
|`trustURLParameters`|Opcional.  El valor predeterminado es `false`.  Si es `true`, permite que la dirección URL incluya parámetros de cadena de consulta que se pasan a la aplicación, de forma similar a los argumentos de línea de comandos que se pasan a una aplicación de línea de comandos.  Para obtener más información, vea [Cómo: Recuperar información de la cadena de consulta de una aplicación ClickOnce en línea](../deployment/how-to-retrieve-query-string-information-in-an-online-clickonce-application.md).<br /><br /> Si el atributo `disallowUrlActivation` es `true`, `trustUrlParameters` se debe excluir del manifiesto o establecer explícitamente en `false`.|  
  
 El elemento `deployment` contiene asimismo los siguientes elementos secundarios.  
  
## suscripción  
 Opcional.  Contiene el elemento `update`.  El elemento `subscription` no tiene atributos.  Si el elemento `subscription` no existe, la aplicación [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] no detectará actualizaciones.  Si el atributo `install` del elemento `deployment` es `false`, el elemento `subscription` se omite, ya que una aplicación [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] iniciada desde la red utiliza siempre la última versión.  
  
## update  
 Obligatorio.  Este elemento es secundario del elemento `subscription` y contiene `beforeApplicationStartup` o el elemento `expiration`.  `beforeApplicationStartup` y `expiration` no se pueden especificar en el mismo manifiesto de implementación.  
  
 El elemento `update` no tiene atributos.  
  
## beforeApplicationStartup  
 Opcional.  Es un elemento secundario del elemento `update` y no tiene atributos.  Si existe el elemento `beforeApplicationStartup`, la aplicación se bloqueará cuando [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] compruebe si hay actualizaciones, en caso de que el cliente esté en línea.  Si este elemento no existe, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] detectará primero las actualizaciones basadas en los valores especificados para el elemento `expiration`.  `beforeApplicationStartup` y `expiration` no se pueden especificar en el mismo manifiesto de implementación.  
  
## expiration  
 Opcional.  Es un elemento secundario del elemento `update` y no tiene elementos secundarios.  `beforeApplicationStartup` y `expiration` no se pueden especificar en el mismo manifiesto de implementación.  Cuando se produce la comprobación de actualizaciones y se detecta una versión actualizada, la nueva versión se almacena en memoria caché mientras se ejecuta la versión existente.  A continuación, la nueva versión se instala en el inicio siguiente de la aplicación [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  
  
 El elemento `expiration` admite los siguientes atributos.  
  
|Atributo|Descripción|  
|--------------|-----------------|  
|`maximumAge`|Obligatorio.  Identifica la antigüedad que debe tener la actualización actual antes de que la aplicación realice una comprobación.  La unidad de tiempo se determina mediante el atributo `unit`.|  
|`unit`|Obligatorio.  Identifica la unidad de tiempo de `maximumAge`.  Las unidades válidas son `horas`, `días` y `semanas`.|  
  
## deploymentProvider  
 Para .NET Framework 2.0, este elemento es obligatorio si el manifiesto de implementación contiene una sección `subscription`.  Para .NET Framework 3.5 y versiones posteriores, este elemento es opcional y tiene como valor predeterminado la ruta de acceso del servidor y del archivo donde se detectó el manifiesto de implementación.  
  
 Este elemento es un elemento secundario del elemento `deployment` y tiene el atributo siguiente:  
  
|Atributo|Descripción|  
|--------------|-----------------|  
|`codebase`|Obligatorio.  Identifica la ubicación, como un identificador uniforme de recursos \(URI\), del manifiesto de implementación que se utiliza para actualizar la aplicación [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  Este elemento también permite reenviar las ubicaciones de actualización para las instalaciones basadas en CD.  Debe ser un URI válido.|  
  
## Comentarios  
 Puede configurar la aplicación [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] para que detecte actualizaciones durante el inicio, después del inicio, o nunca.  Para buscar actualizaciones durante el inicio, asegúrese de que haya un elemento `beforeApplicationStartup` bajo el elemento `update`.  Para buscar actualizaciones después del inicio, asegúrese de haya un elemento `expiration` bajo el elemento `update` y de que se proporcionen los intervalos de actualización.  
  
 Para deshabilitar la comprobación de actualizaciones, quite el elemento `subscription`.  Aunque en el manifiesto de implementación se especifique que no se busquen nunca actualizaciones, podrá buscarlas manualmente mediante el método <xref:System.Deployment.Application.ApplicationDeployment.CheckForUpdate%2A>.  
  
 Para obtener más información acerca de cómo se relaciona deploymentProvider con las actualizaciones, vea [Elegir una estrategia de actualización de ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md).  
  
## Ejemplos  
 En el siguiente ejemplo de código se muestra un elemento `deployment` en un manifiesto de implementación [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  En este ejemplo se utiliza un elemento `deploymentProvider` para indicar la ubicación de actualización preferida.  
  
```  
<deployment install="true" minimumRequiredVersion="2.0.0.0" mapFileExtension="true" trustUrlParameters="true">  
    <subscription>  
      <update>  
        <expiration maximumAge="6" unit="hours" />  
      </update>  
    </subscription>  
    <deploymentProvider codebase="http://www.adatum.com/MyApplication.application" />  
  </deployment>  
```  
  
## Vea también  
 [Manifiesto de la implementación ClickOnce](../deployment/clickonce-deployment-manifest.md)