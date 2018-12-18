---
title: 'Cómo: comprobar la configuración de la propiedad IIS | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- IIS, property settings
- debugging Web applications, troubleshooting
- IIS administration tool
- Web applications, setting properties
- properties [debugger], setting with IIS administration tool
ms.assetid: 9efc50bf-02fb-4750-9b3e-f03c38f10d8b
caps.latest.revision: 15
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4639055fe9320c8fd1bf1b2575bca323642dd17f
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51742078"
---
# <a name="how-to-verify-iis-property-settings"></a>Cómo: Comprobar los valores de configuración de la propiedad IIS
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Se pueden establecer las propiedades de una aplicación Web utilizando la herramienta de administración de IIS. Estas propiedades deben establecerse correctamente para que se ejecute la aplicación, por lo que la comprobación de esta configuración es a menudo un paso necesario en la solución de problemas.  
  
> [!NOTE]
>  Los cuadros de diálogo y comandos de menú que se ven pueden diferir de los descritos en la Ayuda, en función de los valores de configuración o de edición activos. Para cambiar la configuración, elija la opción **Importar y exportar configuraciones** del menú **Herramientas** . Para obtener más información, consulte [Personalizar la configuración de desarrollo en Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-check-iis-settings-for-the-web-application"></a>Para comprobar la configuración de IIS para la aplicación Web  
  
1.  Abra el **herramientas administrativas** ventana: en el **iniciar** menú, elija **programas**y, a continuación, haga clic en **herramientas administrativas**. Si **herramientas administrativas** no aparece en el **programas** menú y, a continuación, busque en el **Panel de Control**.  
  
    -   En Windows 2000, seleccione **Administrador de servicios Internet**.  
  
    -   En Windows XP, seleccione **Internet Information Services**.  
  
    -   En Windows Server 2003, haga doble clic en **Administre su servidor**.  
  
         El **Administre su servidor** abre la ventana. En **Application Server**, haga clic en **administrar este servidor de aplicaciones**.  
  
         El **Application Server** abre la ventana. Abra el **Internet Information Services (IIS) Manager** nodo en el panel izquierdo.  
  
2.  En el cuadro de diálogo, haga clic en el nodo de control de árbol correspondiente a su equipo. Haga clic en el **sitios Web** nodo y seleccione el nodo de la aplicación Web. Será un nodo de sitio Web y, por tanto, un elemento relacionado de la **sitio Web predeterminado** nodo o un nodo del directorio virtual debajo de un nodo de sitio Web existente.  
  
3.  Haga clic en la aplicación Web y, en el menú contextual, haga clic en **propiedades**.  
  
4.  Compruebe la configuración de seguridad de la aplicación Web:  
  
    1.  En la aplicación Web **propiedades** ventana, haga clic en el **seguridad de directorios** ficha y haga clic en **editar**.  
  
    2.  En el **métodos de autenticación** cuadro de diálogo, seleccione **habilitar el acceso anónimo** y **autenticación de Windows integrada** si ya no están seleccionados.  
  
    3.  Haga clic en **Aceptar** para cerrar el **métodos de autenticación** cuadro de diálogo.  
  
5.  Para una aplicación de servidor ATL, compruebe que el verbo DEBUG está asociado con la extensión ISAPI. Para obtener más información, consulte [Cómo: asociar el verbo de depuración con la extensión](http://msdn.microsoft.com/en-us/50d261d3-4bd4-41c0-b44e-3591086f121e).  
  
6.  Para un [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] aplicación, asegúrese de que la carpeta virtual de la aplicación tiene un nombre de aplicación establecido en **Internet Information Services (IIS) Manager**, **Administrador de servicios Internet** o  **Servicios de Internet Information Server**.  
  
    1.  En la aplicación Web **propiedades** ventana, seleccione el **Directory** ficha, si la aplicación está en un directorio virtual, o la **Home Directory** ficha, si la aplicación está en un sitio Web.  
  
    2.  Compruebe que el nombre de la **ruta de acceso Local** coincide con el nombre del directorio donde se implementó la aplicación.  
  
    3.  En **configuración de la aplicación**, escriba el nombre del directorio raíz que contiene la aplicación.  
  
    4.  Haga clic en **Aceptar** para cerrar el **propiedades** cuadro de diálogo.  
  
7.  Para un [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] aplicación, haga clic en el **ASP.NET** ficha y compruebe que la versión correcta de [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] se especifica.  
  
8.  Haga clic en **Aceptar** para cerrar el **propiedades** cuadro de diálogo.  
  
9. Haga clic en **Aceptar** para cerrar el **Internet Information Services (IIS) Manager**, **Administrador de servicios Internet**, o **Internet Information Services**cuadro de diálogo.  
  
## <a name="see-also"></a>Vea también  
 [Solución de problemas](../debugger/debugging-web-applications-troubleshooting.md)



