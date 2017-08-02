---
title: "C&#243;mo: Marcar los controles como seguros"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "controles seguros [desarrollo de SharePoint en Visual Studio]"
  - "desarrollo de SharePoint en Visual Studio, herramientas para paquetes avanzadas"
  - "desarrollo de SharePoint en Visual Studio, controles seguros"
ms.assetid: 813727d5-6750-407c-a23e-c38dd611e78c
caps.latest.revision: 16
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 15
---
# C&#243;mo: Marcar los controles como seguros
  Por motivos de seguridad, SharePoint diferencia entre los controles web que están protegidos contra la inyección de script y los controles web que no lo están.  Los usuarios que no son de confianza pueden obtener acceso a los controles protegidos o *controles seguros*.  Puede marcar los controles como seguros en la propiedad Safe Control Entries de un elemento de proyecto de SharePoint o en el **Diseñador de paquetes** al agregar un ensamblado al paquete.  Para obtener más información, vea  
  
 [cambian los valores del archivo web.config](http://go.microsoft.com/fwlink/?LinkId=178965) y [Registrar un ensamblado de elementos web como Control entries](http://go.microsoft.com/fwlink/?LinkId=171013).  
  
> [!IMPORTANT]  
>  Estos procedimientos se usan con fines ilustrativos.  Marque los controles como seguros solamente si tiene la seguridad de que son seguros.  
  
## Marcar controles como seguros en la propiedad Safe Control Entries  
  
#### Para marcar controles como seguros o no seguros en la propiedad Safe Control Entries  
  
1.  Cree una solución de SharePoint con un proyecto de elemento web visual.  
  
2.  Agregue dos controles al elemento web: un cuadro de texto y un botón.  Deje los nombres en sus valores predeterminados, TextBox1 y Button1, respectivamente.  
  
3.  Agregue dos entradas a la propiedad **Safe Control Entries** del elemento web.  Para ello, elija el botón de puntos suspensivos \(![Elipse del Diseñador de ASP.NET Mobile](~/docs/sharepoint/media/mwellipsis.gif "Elipse del Diseñador de ASP.NET Mobile")\) situado junto a la propiedad de **Entradas de controles seguros** en la ventana de **Propiedades** .  
  
     Se abrirá el cuadro de diálogo **Entradas de controles seguros**.  
  
4.  En el cuadro de diálogo de **Entradas de controles seguros** , elija el botón de **Add** dos veces para agregar dos entradas de controles seguros al panel de **Miembros** : una para el botón y otra para el cuadro de texto.  
  
5.  Elija la primera entrada de control seguro, y después cambie el valor de la propiedad de **Seguro** a **False**, de su propiedad de **Nombre de tipo** a **Botón1**, y su propiedad de **Protección frente a scripts** a **False**.  
  
     En este paso es donde el control de botón se identifica como control no seguro.  
  
6.  Elija la segunda entrada de control seguro en la lista.  Deje el valor de la propiedad de **Seguro** como **VERDADERO** y establezca su propiedad de **Nombre de tipo** a **TextBox1** y su propiedad de **Protección frente a scripts** a **VERDADERO**.  
  
     El control de cuadro de texto se marca ahora como un control seguro contra la inyección de script.  
  
7.  Elija el botón **Aceptar** para cerrar el cuadro de diálogo.  
  
## Marcar los controles como seguros en el Diseñador de paquetes  
  
#### Para marcar los controles como seguros o no seguros en el Diseñador de paquetes  
  
1.  Cree una solución de SharePoint con un proyecto de elemento web visual.  
  
2.  Agregue dos controles al elemento web: un cuadro de texto y un botón.  Deje los nombres en sus valores predeterminados, TextBox1 y Button1, respectivamente.  
  
     Recuerde el espacio de nombres del control porque lo utilizaremos más adelante.  
  
3.  En la barra de menú, elija **Compilación**, **Compilar solución** para compilar el proyecto.  
  
4.  Cree otra solución de SharePoint.  
  
5.  En **Explorador de soluciones**, abra el menú contextual para el archivo Package.Package y, a continuación **Abierta** para abrir **Diseñador de paquetes**.  
  
6.  En **Diseñador de paquetes**, elija la ficha de **opciones avanzadas** .  
  
7.  En **Ensamblados adicionales**, elija el botón de **Add** , y elija **Agregar ensamblado existente** de la lista.  
  
8.  En el cuadro de diálogo de **Agregar ensamblado existente** , elija el botón de puntos suspensivos \(![Elipse del Diseñador de ASP.NET Mobile](~/docs/sharepoint/media/mwellipsis.gif "Elipse del Diseñador de ASP.NET Mobile")\) situado junto a **Ruta de acceso de origen**.  
  
9. Elija el ensamblado de la solución de SharePoint que creó en el paso 1, y elija el botón de **Abierta** .  
  
10. En este ejemplo, deje la opción **Destino de la implementación** como GlobalAssemblyCache.  
  
     Este paso hace que el ensamblado se implemente en la memoria caché global de ensamblados del sistema.  Si desea que el ensamblado se implemente en la carpeta \(Bin\) de la aplicación web, seleccione en su lugar esa opción.  Para obtener más información, vea [Elementos de implementación web en la base de SharePoint](http://go.microsoft.com/fwlink/?LinkId=177509).  
  
11. En el cuadro de **Controles seguros** , elija el botón de **Haga clic aquí para agregar un nuevo elemento** .  
  
12. Especifique los valores para las propiedades de la tabla siguiente.  
  
    |Nombre de la propiedad|Valor|  
    |----------------------------|-----------|  
    |Espacio de nombres|Espacio de nombres completo del control, por ejemplo **BdcModelProject1.VisualWebPart1**.|  
    |Nombre de tipo|Button1|  
    |Nombre del ensamblado|Nombre seguro, por ejemplo, Microsoft.Office.SharePoint.ClientExtensions, Version\=14.0.0.0, Culture\=neutral, PublicKeyToken\=71e9bce111e9429c.|  
    |Safe|Desactive la casilla **Safe**.|  
    |Safe Against Script|Deje desactivada la casilla **Safe Against Script**.|  
  
    > [!NOTE]  
    >  El valor **Assembly Name** de los ensamblados agregados a través de la pestaña **Avanzadas** del **Diseñador de paquetes** no puede ser un token, debe ser un ensamblado con nombre seguro.  Para obtener más información, vea [La creación y ensamblados Fuerte\- denominadas Utilizar](http://go.microsoft.com/fwlink/?LinkId=177513).  
  
13. Elija la tecla TAB para crear otra entrada de control seguro.  
  
14. Elija el botón de **Haga clic aquí para agregar un nuevo elemento** de nuevo.  
  
15. Especifique los valores para las propiedades de la tabla siguiente.  
  
    |Nombre de la propiedad|Valor|  
    |----------------------------|-----------|  
    |Espacio de nombres|Espacio de nombres completo del control, por ejemplo **BdcModelProject1.VisualWebPart1**.|  
    |Nombre de tipo|TextBox1|  
    |Nombre del ensamblado|Nombre seguro, por ejemplo, Microsoft.Office.SharePoint.ClientExtensions, Version\=14.0.0.0, Culture\=neutral, PublicKeyToken\=71e9bce111e9429c.|  
    |Safe|Active la casilla **Safe**.|  
    |Safe Against Script|Active la casilla **Safe Against Script**.|  
  
16. Elija la tecla TAB, y elija el botón de **Aceptar** para cerrar el cuadro de diálogo.  
  
## Vea también  
 [Proporcionar información de empaquetado e implementación en los elementos del proyecto](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)   
 [Empaquetar e implementar soluciones de SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
  