---
title: "Cómo: marcar los controles como controles seguros | Documentos de Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, safe controls
- SharePoint development in Visual Studio, advanced packaging tools
- safe controls [SharePoint development in Visual Studio]
ms.assetid: 813727d5-6750-407c-a23e-c38dd611e78c
caps.latest.revision: "16"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: bd659a1df9782c4e16dd2664a27a87e858e54ef2
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-mark-controls-as-safe-controls"></a>Cómo: Marcar los controles como seguros
  Para la seguridad, SharePoint diferencia entre los controles Web que están protegidos contra la inyección de script y los controles Web que no están. Botones, protegidos o *controles seguros*, puede tener acceso a los usuarios de confianza. Puede marcar los controles como seguros en la propiedad Safe Control Entries de un elemento de proyecto de SharePoint o en el **Diseñador de paquetes** cuando se agrega un ensamblado al paquete. Para obtener más información, consulte  
  
 [el archivo Web.config el cambio de configuración](http://go.microsoft.com/fwlink/?LinkId=178965) y [registrar un ensamblado de elemento Web como un Control seguro](http://go.microsoft.com/fwlink/?LinkId=171013).  
  
> [!IMPORTANT]  
>  Estos procedimientos son con fines ilustrativos. Marque los controles como seguros solamente si está seguro de que están protegidos.  
  
## <a name="marking-safe-controls-in-the-safe-control-entries-property"></a>Marcar los controles como seguros en la propiedad de las entradas de controles seguros  
  
#### <a name="to-mark-controls-as-safe-or-unsafe-in-the-safe-control-entries-property"></a>Para marcar controles como seguros o no seguros en la propiedad de entradas de controles seguros  
  
1.  Crear una solución de SharePoint con un proyecto de elemento Web Visual.  
  
2.  Agregue dos controles al elemento Web: un cuadro de texto y un botón. Deje los nombres en sus valores predeterminados, TextBox1 y Button1, respectivamente.  
  
3.  Agregue dos entradas para el elemento Web **entradas de controles seguros** propiedad. Para ello, elija el botón de puntos suspensivos (![elipse del Diseñador de ASP.NET Mobile](../sharepoint/media/mwellipsis.gif "elipse del Diseñador de ASP.NET Mobile")) situado junto a la **entradas de controles seguros** propiedad en el  **Propiedades** ventana.  
  
     El **entradas de controles seguros** aparece el cuadro de diálogo.  
  
4.  En el **entradas de controles seguros** diálogo cuadro, elija la **agregar** botón dos veces para agregar dos entradas de controles seguros para la **miembros** panel: uno para el botón y otro para el cuadro de texto.  
  
5.  Elija la primera entrada de control seguro y, a continuación, cambie el valor de su **seguro** propiedad **False**, sus **nombre de tipo** propiedad **Button1**y su **Safe Against Script** propiedad **False**.  
  
     Este paso identifica el control de botón como un control no es seguro.  
  
6.  Seleccione la segunda entrada de control seguro en la lista. Deje el valor de su **seguro** propiedad como **True** y establecer su **nombre de tipo** propiedad **TextBox1** y su **seguro En la secuencia de comandos** propiedad **True**.  
  
     Ahora, el control de cuadro de texto se marca como un control que es seguro contra la inyección de script.  
  
7.  Elija el botón **Aceptar** para cerrar el cuadro de diálogo.  
  
## <a name="marking-safe-controls-in-the-package-designer"></a>Marcar los controles como seguros en el Diseñador de paquetes  
  
#### <a name="to-mark-controls-as-safe-or-unsafe-in-the-package-designer"></a>Para marcar los controles como seguros o no seguros en el Diseñador de paquetes  
  
1.  Crear una solución de SharePoint con un proyecto de elemento Web Visual.  
  
2.  Agregue dos controles al elemento Web: un cuadro de texto y un botón. Deje los nombres en sus valores predeterminados, TextBox1 y Button1, respectivamente.  
  
     Tome nota del espacio de nombres del control porque se utiliza más adelante.  
  
3.  En la barra de menús, elija **generar**, **generar solución** para compilar el proyecto.  
  
4.  Cree otra solución de SharePoint.  
  
5.  En **el Explorador de soluciones**, abra el menú contextual para el archivo Package.Package y, a continuación, elija **abrir** para abrir el **Diseñador de paquetes**.  
  
6.  En el **Diseñador de paquetes**, elija la **avanzadas** ficha.  
  
7.  En **ensamblados adicionales**, elija la **agregar** botón y, a continuación, elija **Agregar ensamblado existente** en la lista.  
  
8.  En el **Agregar ensamblado existente** diálogo cuadro, elija el botón de puntos suspensivos (![elipse del Diseñador de ASP.NET Mobile](../sharepoint/media/mwellipsis.gif "elipse del Diseñador de ASP.NET Mobile")) situado junto a  **Ruta de acceso de origen**.  
  
9. Elija el ensamblado de la solución de SharePoint que ha creado en el paso 1 y, a continuación, elija la **abiertos** botón.  
  
10. En este ejemplo, deje el **destino de implementación** opción como GlobalAssemblyCache.  
  
     Este paso hace que el ensamblado que se va a implementar en la caché de ensamblados Global (GAC) del sistema. Si desea que el ensamblado que se va a implementar en la carpeta (Bin) de la aplicación Web, seleccione esta opción en su lugar. Para obtener más información, consulte [implementar elementos Web en SharePoint Foundation](http://go.microsoft.com/fwlink/?LinkId=177509).  
  
11. En el **controles seguros** cuadro, elija la **haga clic aquí para agregar un nuevo elemento** botón.  
  
12. Escriba los valores para las propiedades de la tabla siguiente.  
  
    |Nombre de la propiedad|Valor|  
    |-------------------|-----------|  
    |Espacio de nombres|El espacio de nombres completo para el control, como **BdcModelProject1.VisualWebPart1**.|  
    |Nombre de tipo|Button1|  
    |Nombre del ensamblado|Un nombre seguro, como: ejemplo, versión = 14.0.0.0, Culture = neutral, PublicKeyToken = 71e9bce111e9429c.|  
    |Seguridad de|Desactive el **seguro** casilla de verificación.|  
    |Seguridad de secuencia de comandos|Deje el **Safe Against Script** casilla de verificación.|  
  
    > [!NOTE]  
    >  El **nombre del ensamblado** valor de los ensamblados agregados a través de la **avanzadas** pestaña de la **Diseñador de paquetes** no puede ser un token, debe ser un ensamblado con nombre seguro. Para obtener más información, vea [Crear y utilizar ensamblados con nombre seguro](http://go.microsoft.com/fwlink/?LinkId=177513).  
  
13. Elija la tecla Tab para crear otra entrada de control seguro.  
  
14. Elija la **haga clic aquí para agregar un nuevo elemento** nuevamente en el botón.  
  
15. Escriba los valores para las propiedades de la tabla siguiente.  
  
    |Nombre de la propiedad|Valor|  
    |-------------------|-----------|  
    |Espacio de nombres|El espacio de nombres completo para el control, como **BdcModelProject1.VisualWebPart1**.|  
    |Nombre de tipo|TextBox1|  
    |Nombre del ensamblado|Un nombre seguro, como: ejemplo, versión = 14.0.0.0, Culture = neutral, PublicKeyToken = 71e9bce111e9429c.|  
    |Seguridad de|Seleccione el **seguro** casilla de verificación.|  
    |Seguridad de secuencia de comandos|Seleccione el **Safe Against Script** casilla de verificación.|  
  
16. Elija la tecla Tab y, a continuación, elija la **Aceptar** botón para cerrar el cuadro de diálogo.  
  
## <a name="see-also"></a>Vea también  
 [Proporcionar información empaquetado e implementación de elementos de proyecto](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)   
 [Empaquetar e implementar soluciones de SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
  