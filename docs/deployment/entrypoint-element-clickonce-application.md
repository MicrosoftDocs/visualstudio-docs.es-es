---
title: "Elemento &lt;entryPoint&gt; (Aplicaci&#243;n ClickOnce) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "urn:schemas-microsoft-com:asm.v2#commandLine"
  - "urn:schemas-microsoft-com:asm.v2#entryPoint"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "<entryPoint> (elemento) [manifiesto de aplicación ClickOnce]"
  - "manifiestos [ClickOnce], entryPoint (elemento)"
ms.assetid: 10ad3083-10c1-4189-a870-9bba2eab244f
caps.latest.revision: 33
caps.handback.revision: 33
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Elemento &lt;entryPoint&gt; (Aplicaci&#243;n ClickOnce)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Identifica el ensamblado que se debe ejecutar cuando esta aplicación [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] se ejecuta en un equipo cliente.  
  
## Sintaxis  
  
```  
  
      <entryPoint  
   name  
>  
   <assemblyIdentity  
      name  
      version  
      processorArchitecture  
      language  
   />  
   <commandLine  
      file  
      parameters  
   />  
   <customHostRequired />  
   <customUX />  
</entryPoint>  
```  
  
## Elementos y atributos  
 Se requiere el elemento `entryPoint`, que se encuentra en el espacio de nombres `urn:schemas-microsoft-com:asm.v2`.  Puede haber sólo uno elemento `entryPoint` definido en un manifiesto de aplicación.  
  
 El elemento `entryPoint` tiene el siguiente atributo.  
  
|Atributo|Descripción|  
|--------------|-----------------|  
|`name`|Opcional.  .NET Framework no utiliza este valor.|  
  
 `entryPoint` tiene los elementos siguientes.  
  
## assemblyIdentity  
 Obligatorio.  El rol de `assemblyIdentity` y sus atributos se define en [Elemento \<assemblyIdentity\>](../deployment/assemblyidentity-element-clickonce-application.md).  
  
 El atributo `processorArchitecture` de este elemento y el atributo `processorArchitecture`, definidos en `assemblyIdentity` en alguna parte del manifiesto de aplicación, deben coincidir.  
  
## commandLine  
 Obligatorio.  Debe ser un elemento secundario del elemento `entryPoint`.  No tiene ningún elemento secundario y tiene los atributos siguientes.  
  
|Atributo|Descripción|  
|--------------|-----------------|  
|`file`|Obligatorio.  Referencia local al ensamblado de inicio para la aplicación [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  Este valor no puede contener separadores de ruta de acceso de barra diagonal \(\/\) o de barra diagonal inversa \(\\\).|  
|`parameters`|Obligatorio.  Describe la acción que se llevará a cabo con el punto de entrada.  El único valor válido es `run`; si se proporciona una cadena vacía, se supone el valor `run`.|  
  
## customHostRequired  
 Opcional.  Si está incluido, especifica que esta implementación contiene un componente que se implementará dentro de un host personalizado, y no es una aplicación independiente.  
  
 Si este elemento está presente, los elementos `commandLine` y `assemblyIdentity` no deben estar presentes.  Si están, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] producirá un error de validación durante la instalación.  
  
 Este elemento no tiene ningún atributo y ningún elemento secundario.  
  
## customUX  
 Opcional.  Especifica que un instalador personalizado instala y mantiene la aplicación, y que no se crea ninguna entrada del menú Inicio, acceso directo o entrada de Agregar o quitar programas.  
  
```  
<customUX xmlns="urn:schemas-microsoft-com:clickonce.v1" />  
```  
  
 Una aplicación que incluye el elemento customUX debe proporcionar un instalador personalizado que utiliza la clase <xref:System.Deployment.Application.InPlaceHostingManager> para realizar las operaciones de la instalación.  Una aplicación con este elemento no se puede instalar haciendo doble clic en su arranque de requisito previo de setup.exe o de manifiesto.  El instalador personalizado puede crear entradas del menú Inicio, accesos directos y entradas de Agregar o quitar programas.  Si el instalador personalizado no crea una entrada Agregar o quitar programas, deberá almacenar el identificador de suscripción proporcionado por la propiedad <xref:System.Deployment.Application.GetManifestCompletedEventArgs.SubscriptionIdentity%2A> y habilitar al usuario para desinstalar posteriormente la aplicación mediante una llamada al método <xref:System.Deployment.Application.InPlaceHostingManager.UninstallCustomUXApplication%2A>.  Para obtener más información, vea [Tutorial: Crear un instalador personalizado para una aplicación ClickOnce](../deployment/walkthrough-creating-a-custom-installer-for-a-clickonce-application.md).  
  
## Comentarios  
 Este elemento identifica el ensamblado y el punto de entrada de la aplicación [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  
  
 No se puede utilizar `commandLine` para pasar parámetros en su aplicación en tiempo de ejecución.  Puede tener acceso a los parámetros de cadena de consulta de una implementación de [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] desde el <xref:System.AppDomain> de la aplicación.  Para obtener más información, vea [Cómo: Recuperar información de la cadena de consulta de una aplicación ClickOnce en línea](../deployment/how-to-retrieve-query-string-information-in-an-online-clickonce-application.md).  
  
## Ejemplo  
 En el siguiente ejemplo de código se muestran un elemento `entryPoint` de un manifiesto de aplicación para una aplicación [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  Este ejemplo de código forma parte de un ejemplo más extenso que aparece en el tema [Manifiesto de aplicación ClickOnce](../deployment/clickonce-application-manifest.md).  
  
```  
<!-- Identify the main code entrypoint. -->  
<!-- This code runs the main method in an executable assembly. -->  
  <entryPoint>  
    <assemblyIdentity   
      name="MyApplication"   
      version="1.0.0.0"  
      language="neutral"  
      processorArchitecture="x86" />  
    <commandLine file="MyApplication.exe" parameters="" />  
  </entryPoint>  
```  
  
## Vea también  
 [Manifiesto de aplicación ClickOnce](../deployment/clickonce-application-manifest.md)