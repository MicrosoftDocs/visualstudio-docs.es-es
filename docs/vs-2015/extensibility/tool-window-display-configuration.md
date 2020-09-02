---
title: Configuración de pantalla de la ventana de herramientas | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- tool windows, configuring
- tool windows, appearance
ms.assetid: 502a4926-bb83-473e-94e2-8e833c5f8b53
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 1af78bd58c42cf1312e36621011802e908c9e919
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68186392"
---
# <a name="tool-window-display-configuration"></a>Configuración para mostrar de la ventana de herramientas
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Cuando un VSPackage registra una ventana de herramientas, la posición, el tamaño, el estilo de acoplamiento y la información de visibilidad predeterminados se especifican en los valores opcionales. Para obtener más información sobre el registro de ventanas de herramientas, vea [ventanas de herramientas en el registro](../extensibility/tool-windows-in-the-registry.md) .  
  
## <a name="window-display-information"></a>Información de presentación de ventana  
 La configuración de presentación básica de una ventana de herramientas se almacena en un máximo de seis valores opcionales:  
  
```  
HKEY_LOCAL_MACHINE\  
  Software\  
    Microsoft\  
      VisualStudio\  
        <Version>\  
          ToolWindows\  
            <Tool Window GUID>\  
              (Default)       = reg_sz: <Package GUID>Name            = reg_sz: <name of tool window>Float           = reg_sz: <position>Style           = reg_sz: <dock style>Window          = reg_sz: <window GUID>Orientation     = reg_sz: <orientation>DontForceCreate = reg_dword: 0x00000000  
```  
  
|Nombre|Tipo|data|Descripción|  
|----------|----------|----------|-----------------|  
|Nombre|REG_SZ|"El nombre corto va aquí"|Nombre corto que describe la ventana de herramientas. Solo se usa como referencia en el registro.|  
|Float|REG_SZ|"X1, Y1, X2, Y2"|Cuatro valores separados por comas. X1, Y1 es la coordenada de la esquina superior izquierda de la ventana de herramientas. X2, Y2 es la coordenada de la esquina inferior derecha. Todos los valores están en coordenadas de pantalla.|  
|Estilo|REG_SZ|INHALA<br /><br /> Flot<br /><br /> Conecta<br /><br /> Fichas<br /><br /> "AlwaysFloat"|Palabra clave que especifica el estado de presentación inicial de la ventana de herramientas.<br /><br /> "MDI" = acoplado con la ventana MDI.<br /><br /> "Float" = flotante.<br /><br /> "Vinculado" = vinculado a otra ventana (que se especifica en la entrada de la ventana).<br /><br /> "Con pestañas" = combinada con otra ventana de herramientas.<br /><br /> "AlwaysFloat" = no se puede acoplar.<br /><br /> Para obtener más información, vea la sección Comentarios a continuación.|  
|Periodo|REG_SZ|*\<GUID>*|El GUID de una ventana a la que se puede vincular o a la ventana de herramientas. El GUID puede pertenecer a una de sus propias ventanas o a una de las ventanas del [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] IDE.|  
|Orientación|REG_SZ|Salido<br /><br /> Correcta<br /><br /> Primeras<br /><br /> Descendente|Vea la sección Comentarios a continuación.|  
|DontForceCreate|REG_DWORD|0 o 1|Cuando esta entrada está presente y su valor no es cero, la ventana se carga, pero no se muestra inmediatamente.|  
  
### <a name="comments"></a>Comentarios  
 La entrada de orientación define la posición en la que se acopla la ventana de herramientas cuando se hace doble clic en la barra de título. La posición es relativa a la ventana especificada en la entrada de la ventana. Si la entrada de estilo se establece en "vinculada", la entrada de orientación puede ser "left", "Right", "Top" o "Bottom". Si la entrada de estilo es "con pestañas", la entrada de orientación puede ser "left" o "Right" y especifica dónde se agrega la pestaña. Si la entrada de estilo es "Float", la ventana de herramientas flota primero. Cuando se hace doble clic en la barra de título, se aplican las entradas de orientación y de ventana, y la ventana usa el estilo "con pestañas". Si la entrada de estilo es "AlwaysFloat", no se puede acoplar la ventana de herramientas. Si la entrada de estilo es "MDI", la ventana de herramientas está vinculada al área MDI y se omite la entrada de la ventana.  
  
### <a name="example"></a>Ejemplo  
  
```  
HKEY_LOCAL_MACHINE\  
  Software\  
    Microsoft\  
      VisualStudio\  
        8.0Exp\  
          ToolWindows\  
            {A0C5197D-0AC7-4B63-97CD-8872A789D233}\  
              (Default)       = reg_sz: {DA9FB551-C724-11D0-AE1F-00A0C90FFFC3}  
              DontForceCreate = reg_dword: 0x00000000  
              Float           = reg_sz: 100,100,450,300  
              Name            = reg_sz: Bookmarks  
              Orientation     = reg_sz: Left  
              Style           = reg_sz: Tabbed  
              Window          = reg_sz: {34E76E81-EE4A-11D0-00A0C90FFFC3}  
```  
  
## <a name="tool-window-visibility"></a>Visibilidad de la ventana de herramientas  
 Los valores de la subclave de visibilidad opcional determinan la configuración de visibilidad de una ventana de herramientas. Los nombres de los valores se utilizan para almacenar los GUID de comandos que requieren la visibilidad de la ventana. Si se ejecuta el comando, el IDE garantiza que la ventana de herramientas se crea y se hace visible.  
  
```  
HKEY_LOCAL_MACHINE\  
  Software\  
    Microsoft\  
      VisualStudio\  
        <Version>\  
          ToolWindows\  
            <Tool Window GUID>\  
              Visibility\  
                (Default) = reg_sz:  
                <GUID>    = reg_dword:  
                <GUID>    = reg_dword:  
                <GUID>    = reg_sz:  
```  
  
|Nombre|Tipo|data|Descripción|  
|----------|----------|----------|-----------------|  
|(Es el valor predeterminado).|REG_SZ|Ninguno|Deje vacío.|  
|*\<GUID>*|REG_DWORD o REG_SZ|0 o una cadena descriptiva.|Opcional. El nombre de la entrada debe ser el GUID de un comando que requiera visibilidad. El valor solo contiene una cadena informativa. Normalmente, el valor es un `reg_dword` establecido en 0.|  
  
### <a name="example"></a>Ejemplo  
  
```  
HKEY_LOCAL_MACHINE\  
  Software\  
    Microsoft\  
      VisualStudio\  
        8.0Exp\  
          ToolWindows\  
            {EEFA5220-E298-11D0-8F78-00A0C9110057}\  
              Visibility\  
                (Default) = reg_sz:  
                {93694fa0-0397-11d1-9f4e-00a0c911004f} = reg_dword: 0x00000000  
                {9DA22B82-6211-11d2-9561-00600818403B} = reg_dword: 0x00000000  
                {adfc4e66-0397-11d1-9f4e-00a0c911004f} = reg_dword: 0x00000000  
```  
  
## <a name="see-also"></a>Consulte también  
 [Elementos fundamentales de VSPackage](../misc/vspackage-essentials.md)
