---
title: Procedimiento Marcar los controles como seguros | Documentos de Microsoft
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, safe controls
- SharePoint development in Visual Studio, advanced packaging tools
- safe controls [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 0d2dfe0da64abb9540724c05d13b84715a684af0
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2019
ms.locfileid: "60082040"
---
# <a name="how-to-mark-controls-as-safe-controls"></a>Procedimiento Marcar los controles como seguros
  Para la seguridad, SharePoint diferencia entre los controles Web que están protegidos contra la inyección de script y los controles Web que no están. Protegido de los controles, o *controles seguros*, pueden tener acceso a los usuarios de confianza. Puede marcar los controles como seguros en la propiedad de las entradas de Control seguro de un elemento de proyecto de SharePoint o en el **Diseñador de paquetes** cuando agrega un ensamblado para el paquete. Para obtener más información, consulte

- [el archivo Web.config el cambio de configuración](http://go.microsoft.com/fwlink/?LinkId=178965) y [registrar un ensamblado de elemento Web como un Control seguro](http://go.microsoft.com/fwlink/?LinkId=171013).

> [!IMPORTANT]
>  Estos procedimientos son para fines ilustrativos. Marcar los controles seguros solo si está seguro de que son seguros.

## <a name="marking-safe-controls-in-the-safe-control-entries-property"></a>Marcar los controles seguros en la propiedad de las entradas de Control seguro

#### <a name="to-mark-controls-as-safe-or-unsafe-in-the-safe-control-entries-property"></a>Para marcar los controles como seguros o no seguros en la propiedad de las entradas de control seguro

1. Crear una solución de SharePoint con un proyecto de elemento Web Visual.

2. Agregue dos controles para el elemento Web: un cuadro de texto y un botón. Deje los nombres de los valores predeterminados, TextBox1 y Button1, respectivamente.

3. Agregue dos entradas para el elemento Web **entradas de controles seguros** propiedad. Para ello, elija el botón de puntos suspensivos (![elipse del Diseñador de ASP.NET Mobile](../sharepoint/media/mwellipsis.gif "elipse del Diseñador de ASP.NET Mobile")) situado junto a la **entradas de controles seguros** propiedad en el  **Propiedades** ventana.

     El **entradas de controles seguros** aparece el cuadro de diálogo.

4. En el **entradas de controles seguros** diálogo cuadro, elija el **agregar** dos veces para agregar dos entradas de control seguras para la **miembros** panel: uno para el botón y otro para el cuadro de texto.

5. Elija la primera entrada de control segura y, a continuación, cambie el valor de su **seguro** propiedad **False**, sus **nombre de tipo** propiedad **Button1**y su **Safe Against Script** propiedad **False**.

     Este paso identifica el control de botón como un control no seguro.

6. En la lista, seleccione la segunda entrada de control segura. Deje el valor de su **seguro** propiedad como **True** y establezca su **nombre de tipo** propiedad **TextBox1** y su **seguro Frente a scripts** propiedad **True**.

     El control de cuadro de texto se marca ahora como un control que es seguro contra la inyección de script.

7. Elija el botón **Aceptar** para cerrar el cuadro de diálogo.

## <a name="marking-safe-controls-in-the-package-designer"></a>Marcar los controles seguros en el Diseñador de paquetes

#### <a name="to-mark-controls-as-safe-or-unsafe-in-the-package-designer"></a>Para marcar los controles como seguros o no seguros en el Diseñador de paquetes

1. Crear una solución de SharePoint con un proyecto de elemento Web Visual.

2. Agregue dos controles para el elemento Web: un cuadro de texto y un botón. Deje los nombres de los valores predeterminados, TextBox1 y Button1, respectivamente.

     Tome nota del espacio de nombres del control porque se utiliza más adelante.

3. En la barra de menús, elija **compilar** > **compilar solución** para compilar el proyecto.

4. Cree otra solución de SharePoint.

5. En **el Explorador de soluciones**, abra el menú contextual para el *Package.Package* de archivo y, a continuación, elija **abrir** para abrir el **Diseñador de paquetes**.

6. En el **Diseñador de paquetes**, elija el **avanzadas** ficha.

7. En **ensamblados adicionales**, elija el **agregar** botón y, a continuación, elija **Agregar ensamblado existente** en la lista.

8. En el **Agregar ensamblado existente** diálogo cuadro, elija el botón de puntos suspensivos (![elipse del Diseñador de ASP.NET Mobile](../sharepoint/media/mwellipsis.gif "elipse del Diseñador de ASP.NET Mobile")) situado junto a  **Ruta de acceso de origen**.

9. Elija el ensamblado de la solución de SharePoint que ha creado en el paso 1 y, a continuación, elija el **abierto** botón.

10. En este ejemplo, deje el **destino de implementación** opción como GlobalAssemblyCache.

     Este paso hace que el ensamblado se implemente en la memoria caché de ensamblados Global (GAC) del sistema. Si desea que el ensamblado se implemente en la carpeta (Bin) de la aplicación Web, seleccione esa opción en su lugar. Para obtener más información, consulte [implementar elementos Web en SharePoint Foundation](http://go.microsoft.com/fwlink/?LinkId=177509).

11. En el **controles seguros** , seleccione el **haga clic aquí para agregar un nuevo elemento** botón.

12. Especifique los valores para las propiedades de la tabla siguiente.

    |Nombre de la propiedad|Valor|
    |-------------------|-----------|
    |Espacio de nombres|El espacio de nombres completo del control, como **BdcModelProject1.VisualWebPart1**.|
    |Nombre de tipo|Button1|
    |Nombre del ensamblado|Un nombre seguro, como: Microsoft.Office.SharePoint.ClientExtensions, Version=14.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c.|
    |Safe|Desactive el **seguro** casilla de verificación.|
    |Protección frente a scripts|Deje el **Safe Against Script** casilla de verificación.|

    > [!NOTE]
    >  El **nombre del ensamblado** valor de los ensamblados agregados a través de la **avanzadas** pestaña de la **Diseñador de paquetes** no puede ser un token, debe ser un ensamblado con nombre seguro. Para obtener más información, vea [Crear y utilizar ensamblados con nombre seguro](http://go.microsoft.com/fwlink/?LinkId=177513).

13. Elija la **ficha** clave para crear otra entrada de control segura.

14. Elija la **haga clic aquí para agregar un nuevo elemento** nuevamente en el botón.

15. Especifique los valores para las propiedades de la tabla siguiente.

    |Nombre de la propiedad|Valor|
    |-------------------|-----------|
    |Espacio de nombres|El espacio de nombres completo del control, como **BdcModelProject1.VisualWebPart1**.|
    |Nombre de tipo|TextBox1|
    |Nombre del ensamblado|Un nombre seguro, como: Microsoft.Office.SharePoint.ClientExtensions, Version=14.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c.|
    |Safe|Seleccione el **seguro** casilla de verificación.|
    |Protección frente a scripts|Seleccione el **Safe Against Script** casilla de verificación.|

16. Elija la **ficha** clave y, a continuación, elija el **Aceptar** botón para cerrar el cuadro de diálogo.

## <a name="see-also"></a>Vea también
- [Proporcionar información de empaquetado e implementación de elementos de proyecto](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)
- [Paquete e implementar soluciones de SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
