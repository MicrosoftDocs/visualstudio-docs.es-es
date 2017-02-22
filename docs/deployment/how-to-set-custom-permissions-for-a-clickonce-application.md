---
title: "C&#243;mo: Establecer permisos personalizados para una aplicaci&#243;n ClickOnce | Microsoft Docs"
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
  - "aplicaciones ClickOnce, permisos"
  - "permisos, aplicaciones ClickOnce"
ms.assetid: 660459ca-ef73-44a8-b323-610001f63b93
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# C&#243;mo: Establecer permisos personalizados para una aplicaci&#243;n ClickOnce
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Puede implementar una aplicación [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] que use los permisos predeterminados de las zonas de Internet o de la intranet local. Como alternativa, puede crear una zona personalizada para los permisos específicos necesarios para la aplicación. Para ello, personalice los permisos de seguridad en la página **Seguridad** del **Diseñador de proyectos**.  
  
### Para personalizar un permiso  
  
1.  Seleccione un proyecto en el **Explorador de soluciones** y, en el menú **Proyecto**, haga clic en **Propiedades**.  
  
2.  Haga clic en la pestaña **Seguridad**.  
  
3.  Active la casilla **Habilitar configuración de seguridad de ClickOnce**.  
  
4.  Seleccione el botón de la opción **Aplicación de confianza parcial**.  
  
     Los controles de la sección **Permisos de seguridad de ClickOnce** están habilitados.  
  
5.  En la lista desplegable **Zona desde la que se instalará la aplicación**, haga clic en **\(Personalizada\)**.  
  
6.  Haga clic en **Editar XML de permisos**.  
  
     El archivo app.manifest se abrirá en el Editor XML.  
  
7.  Antes del elemento `</applicationRequestMinimum>`, agregue el código XML de los permisos necesarios para la aplicación.  
  
    > [!NOTE]
    >  Puede usar el método `ToXml` de un conjunto de permisos para generar el código XML del manifiesto de la aplicación. Por ejemplo, para generar el XML del conjunto de permisos <xref:System.Security.Permissions.EnvironmentPermission>, llame al método <xref:System.Security.Permissions.EnvironmentPermission.ToXml%2A>. Para obtener más información sobre la estructura del XML del conjunto de permisos, consulte [NIB: How to: Import a Permission Set by Using an XML File](http://msdn.microsoft.com/es-es/dea16b54-c108-408a-ac36-cdc05f746236) \(NIB: Cómo importar un conjunto de permisos mediante un archivo XML\).  
  
## Vea también  
 [Proteger las aplicaciones ClickOnce](../deployment/securing-clickonce-applications.md)   
 [Seguridad de acceso del código para aplicaciones ClickOnce](../deployment/code-access-security-for-clickonce-applications.md)   
 [Proteger las aplicaciones ClickOnce](../deployment/securing-clickonce-applications.md)