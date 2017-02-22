---
title: "C&#243;mo: Especificar una ubicaci&#243;n alternativa para las actualizaciones de la implementaci&#243;n | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "implementación ClickOnce, actualizaciones"
  - "actualización de implementación, ubicaciones alternativas"
ms.assetid: 7faacd35-2638-492d-80f6-6b57e5f820de
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# C&#243;mo: Especificar una ubicaci&#243;n alternativa para las actualizaciones de la implementaci&#243;n
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Puede instalar la aplicación [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] inicialmente desde un CD o recurso compartido de archivos, aunque deberá buscar actualizaciones periódicas en el Web.  Puede especificar una ubicación alternativa para las actualizaciones en el manifiesto de implementación para que la aplicación pueda actualizarse desde el Web tras la instalación inicial.  
  
> [!NOTE]
>  La aplicación debe configurarse para una instalación local si desea utilizar esta característica.  Para obtener más información, vea [Tutorial: Implementar manualmente una aplicación ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md).  Además, si instala una aplicación [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] desde la red, establecer una ubicación alternativa hace que [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] utilice dicha ubicación tanto para la instalación inicial como para todas las actualizaciones subsiguientes.  Si realiza una instalación local de la aplicación \(por ejemplo, desde un CD\), la instalación inicial se llevará a cabo utilizando el soporte original y todas las actualizaciones subsiguientes utilizarán la ubicación alternativa.  
  
### Especificar una ubicación alternativa para las actualizaciones utilizando MageUI.exe \(utilidad basada en formularios Windows Forms\)  
  
1.  Abra un símbolo del sistema de .NET Framework y escriba:  
  
     **mageui.exe**  
  
2.  En el menú **Archivo**, elija **Abrir** para abrir el manifiesto de implementación de la aplicación.  
  
3.  Seleccione la ficha **Opciones de implementación**.  
  
4.  En el cuadro de texto denominado **Iniciar ubicación**, escriba la dirección URL al directorio que contendrá el manifiesto de implementación para las actualizaciones de la aplicación.  
  
5.  Guarde el manifiesto de implementación.  
  
### Especificar una ubicación alternativa para las actualizaciones utilizando Mage.exe  
  
1.  Abra un símbolo del sistema de .NET Framework.  
  
2.  Establezca la ubicación de actualización mediante el comando siguiente.  En este ejemplo, **HelloWorld.exe.application** es la ruta del manifiesto de aplicación [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], que siempre tiene la extensión .application, y **http:\/\/adatum.com\/Update\/Path** es la dirección URL en la que [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] buscará actualizaciones de la aplicación.  
  
     **Mage \-Update HelloWorld.exe.application \-ProviderUrl http:\/\/adatum.com\/Update\/Path**  
  
3.  Guarde el archivo.  
  
    > [!NOTE]
    >  Ahora, debe volver a firmar el archivo con Mage.exe.  Para obtener más información, vea [Tutorial: Implementar manualmente una aplicación ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md).  
  
## Seguridad de .NET Framework  
 Si instala la aplicación desde un soporte sin conexión como un CD y el equipo se encuentra en línea, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] buscará primero en la dirección URL especificada por la etiqueta `<deploymentProvider>` en el manifiesto de implementación para determinar si la ubicación de actualización contiene una versión más reciente de la aplicación.  En caso afirmativo, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] instalará la aplicación directamente desde dicha ubicación en lugar de utilizar el directorio de instalación inicial, y el Common Language Runtime \(CLR\) determinará el nivel de confianza de la aplicación mediante `<deploymentProvider>`.  Si el equipo está sin conexión, o no se puede tener acceso al `<deploymentProvider>`, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] realizará la instalación desde el CD y el CLR concederá la confianza en función del punto de instalación. En el caso de instalación desde un CD, la aplicación obtendrá plena confianza.  Todas las actualizaciones subsiguientes heredarán ese nivel de confianza.  
  
 Todas las aplicaciones [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] que utilicen el `<deploymentProvider>` deberán declarar explícitamente los permisos que necesitan en el manifiesto de aplicación para no recibir distintos niveles de confianza en equipos diferentes.  
  
## Vea también  
 [Tutorial: Implementar manualmente una aplicación ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)   
 [Manifiesto de la implementación ClickOnce](../deployment/clickonce-deployment-manifest.md)   
 [Proteger las aplicaciones ClickOnce](../deployment/securing-clickonce-applications.md)   
 [Elegir una estrategia de actualización de ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md)