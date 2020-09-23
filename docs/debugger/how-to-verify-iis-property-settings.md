---
title: para comprobar los valores de configuración de propiedades de IIS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- IIS, property settings
- debugging Web applications, troubleshooting
- IIS administration tool
- Web applications, setting properties
- properties [debugger], setting with IIS administration tool
ms.assetid: 9efc50bf-02fb-4750-9b3e-f03c38f10d8b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4c883257abf48601f5131bdae239df61ea64ba77
ms.sourcegitcommit: 062615c058d2ff44751e8d0c704ccfa3c5543469
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/22/2020
ms.locfileid: "90851052"
---
# <a name="how-to-verify-iis-property-settings"></a>Procedimiento Comprobar los valores de configuración de la propiedad IIS

Se pueden establecer las propiedades de una aplicación Web utilizando la herramienta de administración de IIS. Estas propiedades deben establecerse correctamente para que se ejecute la aplicación, por lo que la comprobación de esta configuración es a menudo un paso necesario en la solución de problemas.

> [!NOTE]
> Los cuadros de diálogo y comandos de menú que se ven pueden diferir de los descritos en la Ayuda, en función de los valores de configuración o de edición activos. Para cambiar la configuración, elija la opción **Importar y exportar configuraciones** del menú **Herramientas** . Para obtener más información, vea [Restablecer la configuración](../ide/environment-settings.md#reset-settings).

## <a name="to-check-iis-settings-for-the-web-application"></a>Para comprobar la configuración de IIS para la aplicación Web

1. Abra la ventana **Herramientas administrativas**: En menú **Inicio**, seleccione **Programas** y, después, haga clic en **Herramientas administrativas**. Si no aparece **Herramientas administrativas** en el menú **Programas**, búsquelo en el **Panel de control**.

   - En Windows 2000, seleccione **Administrador de servicios Internet**.

   - En Windows XP, seleccione **Internet Information Services**.

   - En Windows Server 2003, haga doble clic en **Administrar su servidor**.

        Se abre la ventana **Administrar su servidor**. En **Servidor de aplicaciones**, haga clic en **Administrar este servidor de aplicaciones**.

        Se abre la ventana **Servidor de aplicaciones**. Abra el nodo **Administrador de Internet Information Services (IIS)** en el panel izquierdo.

2. En el cuadro de diálogo, haga clic en el nodo de control de árbol correspondiente a su equipo. Haga clic en el nodo **Sitios web** y seleccione el nodo de la aplicación web. Será un nodo de sitio web y, por consiguiente, un nodo relacionado del nodo **Sitio web predeterminado**, o un nodo de directorio virtual situado bajo un nodo de sitio web existente.

3. Haga clic con el botón derecho en la aplicación web y, en el menú contextual, haga clic en **Propiedades**.

4. Compruebe la configuración de seguridad de la aplicación Web:

   1. En la ventana **Propiedades** de la aplicación web, haga clic en la ficha **Seguridad de directorios** y haga clic en **Editar**.

   2. En el cuadro de diálogo **Métodos de autenticación**, seleccione **Habilitar el acceso anónimo** y **Autenticación de Windows integrada** si no están seleccionadas.

   3. Haga clic en **Aceptar** para cerrar el cuadro de diálogo **Métodos de autenticación**.

5. Para una aplicación de servidor ATL, compruebe que el verbo DEBUG está asociado con la extensión ISAPI. Para obtener más información, vea [Cómo: para asociar el verbo DEBUG a la extensión](/previous-versions/ms165022(v=vs.100)).

6. Para una aplicación de [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)], asegúrese de que la carpeta virtual de la aplicación tiene un nombre de aplicación configurado en **Administrador de Internet Information Services (IIS)** , **Administrador de servicios Internet** o **Internet Information Services**.

   1. En la ventana **Propiedades** de la aplicación web, seleccione la ficha **Directorio** si la aplicación está en un directorio virtual, o la ficha **Directorio principal** si la aplicación está en un sitio web.

   2. Compruebe que el nombre en **Ruta de acceso local** coincide con el nombre del directorio donde se implementó la aplicación.

   3. En **Configuración de la aplicación**, escriba el nombre del directorio raíz que contiene la aplicación.

   4. Haga clic en **Aceptar** para cerrar el cuadro de diálogo **Propiedades**.

7. En el caso de una aplicación de [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)], haga clic en la ficha **ASP.NET** y compruebe que está especificada la versión correcta de [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)].

8. Haga clic en **Aceptar** para cerrar el cuadro de diálogo **Propiedades**.

9. Haga clic en **Aceptar** para cerrar el cuadro de diálogo **Administrador de Internet Information Services (IIS)** , **Administrador de servicios Internet** o **Internet Information Services**.

## <a name="see-also"></a>Vea también

- [Solución de problemas](../debugger/debugging-web-applications-troubleshooting.md)