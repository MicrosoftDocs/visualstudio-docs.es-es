---
title: "P&#225;gina Seguridad, Dise&#241;ador de proyectos | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vb.ProjectPropertiesSecurity"
  - "vb.XBAPProjectPropertiesSecurity"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "Diseñador de proyectos, página Seguridad"
  - "Página Seguridad en el Diseñador de proyectos"
ms.assetid: 641d9cd3-fa07-498a-8568-3c169bb4d3d5
caps.latest.revision: 34
caps.handback.revision: 34
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# P&#225;gina Seguridad, Dise&#241;ador de proyectos
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

La página **Seguridad** del **Diseñador de proyectos** se utiliza para configurar las opciones de seguridad de acceso del código de las aplicaciones que se implementan mediante [!INCLUDE[ndptecclick](../../deployment/includes/ndptecclick_md.md)].  Para obtener más información, vea [Seguridad de acceso del código para aplicaciones ClickOnce](../../deployment/code-access-security-for-clickonce-applications.md).  
  
 Para tener acceso a la página **Seguridad**, seleccione un nodo de proyecto en el **Explorador de soluciones** y, a continuación, haga clic en la opción **Propiedades** del menú **Proyecto**.  Cuando aparezca el **Diseñador de proyectos**, haga clic en la ficha **Seguridad**.  
  
## Configuración de seguridad  
 **Habilitar configuración de seguridad de ClickOnce**  
 Determina si se habilitará o no la configuración de seguridad en tiempo de diseño.  Si esta opción está desactivada, no estarán disponibles las demás opciones de la página **Seguridad**.  
  
> [!NOTE]
>  Al publicar una aplicación mediante el **Asistente para publicación**, se habilita esta opción automáticamente.  
  
 Si activa esta opción, puede elegir entre dos botones de radio: **Aplicación de plena confianza** o **Aplicación de confianza parcial**.  
  
 De manera predeterminada, para los proyectos de aplicación de explorador web de WPF, esta opción está activada.  
  
 De manera predeterminada, para todos los demás tipos de proyecto, esta opción está desactivada.  
  
 **Aplicación de plena confianza**  
 Si selecciona esta opción, la aplicación solicita los permisos de plena confianza cuando se instala o ejecuta en un equipo cliente.  Evite utilizar la plena confianza si es posible, porque la aplicación recibirá un acceso no restringido a recursos tales como el sistema de archivos y el Registro.  
  
 De manera predeterminada, para los proyectos de aplicación de explorador web de WPF, esta opción se establece en confianza parcial.  
  
 De manera predeterminada, para todos los demás tipos de proyecto, esta opción se establece en plena confianza.  
  
 **Aplicación de confianza parcial**  
 Si selecciona esta opción, la aplicación solicita los permisos de confianza parcial cuando se instala o ejecuta en un equipo cliente.  *Confianza parcial* significa que sólo las acciones que se permiten en los permisos de seguridad de acceso del código solicitados se ejecutarán.  Para obtener más información sobre cómo configurar los permisos de seguridad, vea [Seguridad de acceso del código para aplicaciones ClickOnce](../../deployment/code-access-security-for-clickonce-applications.md).  
  
 Puede especificar la configuración de seguridad de confianza parcial configurando las opciones del área **Permisos de seguridad de ClickOnce**.  
  
## Permisos de seguridad de ClickOnce  
 **Zona desde la que se instalará la aplicación**  
 Especifica un conjunto predeterminado de permisos de seguridad de acceso del código.  Elija **Personalizado** para comenzar sin permisos habilitados, o bien elija **Internet** o **Intranet local** para configurar un conjunto de permisos restringidos.  Si la aplicación solicita más permisos de los concedidos en una zona, aparecerá un mensaje de ClickOnce relativo a la confianza para que el usuario final conceda los permisos adicionales.  Para obtener más información sobre cómo configurar los permisos de seguridad, vea [Seguridad de acceso del código para aplicaciones ClickOnce](../../deployment/code-access-security-for-clickonce-applications.md).  
  
 De manera predeterminada, para los proyectos de aplicación de explorador web de WPF, esta opción se establece en **Internet**.  
  
 **Editar XML de permisos**  
 Abre la plantilla de manifiesto de aplicación \(app.manifest\) para configurar los permisos del conjunto de permisos **\(Personalizado\)**.  
  
 **Avanzado**  
 Abre el [Configuración de seguridad avanzada \(Cuadro de diálogo\)](../../ide/reference/advanced-security-settings-dialog-box.md), que se utiliza para establecer la configuración con el fin de depurar la aplicación con permisos restringidos.  Esta configuración se comprueba durante la depuración y las excepciones de permisos indican que su aplicación puede necesitar más permisos de los definidos en una zona.  
  
## Vea también  
 <xref:System.Security.Permissions.WebBrowserPermission>   
 <xref:System.Security.Permissions.MediaPermission>   
 [Seguridad de acceso del código para aplicaciones ClickOnce](../../deployment/code-access-security-for-clickonce-applications.md)   
 [Cómo: Habilitar la configuración de seguridad para aplicaciones ClickOnce](../../deployment/how-to-enable-clickonce-security-settings.md)   
 [Cómo: Establecer una zona de seguridad para una aplicación ClickOnce](../../deployment/how-to-set-a-security-zone-for-a-clickonce-application.md)   
 [Cómo: Establecer permisos personalizados para una aplicación ClickOnce](../../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md)   
 [Cómo: Depurar una aplicación ClickOnce con permisos restringidos](../../deployment/how-to-debug-a-clickonce-application-with-restricted-permissions.md)   
 [Seguridad e implementación ClickOnce](../../deployment/clickonce-security-and-deployment.md)   
 [Referencia de propiedades del proyecto](../../ide/reference/project-properties-reference.md)   
 [Configuración de seguridad avanzada \(Cuadro de diálogo\)](../../ide/reference/advanced-security-settings-dialog-box.md)