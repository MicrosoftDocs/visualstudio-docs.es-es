---
title: "Configuraci&#243;n de pantalla de ventana de herramienta | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ventanas de herramientas, configurar"
  - "ventanas de herramientas, apariencia"
ms.assetid: 502a4926-bb83-473e-94e2-8e833c5f8b53
caps.latest.revision: 8
caps.handback.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
---
# Configuraci&#243;n de pantalla de ventana de herramienta
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Cuando un paquete VSPackage registra una ventana de herramientas, la posición predeterminada, tamaño, estilo de acoplamiento y otra información de visibilidad se especifica en valores opcionales. Para obtener más información sobre el registro de la ventana de herramienta, consulte [las ventanas de herramientas en el registro](../extensibility/tool-windows-in-the-registry.md)  
  
## <a name="window-display-information"></a>Información de visualización de ventana  
 Configuración de la visualización básica de la ventana de herramienta se almacena en un máximo de seis valores opcionales:  
  
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
  
|Nombre|Tipo|Datos|Descripción|  
|----------|----------|----------|-----------------|  
|Nombre|REG_SZ|"Nombre corto va aquí"|Un nombre corto que describe la ventana de herramientas. Se usa solo como referencia en el registro.|  
|Flotante|REG_SZ|"X1, Y1, X2, Y2"|Cuatro valores separados por comas. X1, Y1 es la coordenada de la esquina superior izquierda de la ventana de herramientas. X2, Y2 es la coordenada de la esquina inferior derecha. Todos los valores están en coordenadas de pantalla.|  
|Estilo|REG_SZ|"MDI"<br /><br /> "Flotar"<br /><br /> "Vinculados"<br /><br /> "Por pestañas"<br /><br /> "AlwaysFloat"|Una palabra clave especifica la inicial Mostrar estado de la ventana de herramientas.<br /><br /> "MDI" = acoplado con ventana MDI.<br /><br /> "Flotar" = flotante.<br /><br /> "Vincular" = vinculada con otra ventana (especificado en la entrada de la ventana).<br /><br /> "Por pestañas" = combina con otra ventana de herramientas.<br /><br /> "AlwaysFloat" = no se puede acoplar.<br /><br /> Para obtener más información, vea la sección Comentarios.|  
|Ventana|REG_SZ|*\< GUID>*|El GUID de una ventana a la que la ventana de herramientas se puede vincular o con pestañas. El GUID puede pertenecer a uno de sus propias ventanas o una de las ventanas de la [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] IDE.|  
|Orientación|REG_SZ|"Izquierda"<br /><br /> "Right"<br /><br /> "Top"<br /><br /> "Bottom"|Vea la sección Comentarios.|  
|DontForceCreate|REG_DWORD|0 o 1|Si esta entrada está presente y su valor no es cero, la ventana se carga, pero no inmediatamente muestra.|  
  
### <a name="comments"></a>Comentarios  
 La entrada de orientación define la posición donde se acopla la ventana de herramientas cuando se hace doble clic en su barra de título. La posición es relativa a la ventana especificada en la entrada de la ventana. Si la entrada de estilo se establece en "Vinculado", la entrada de orientación puede ser "Left", "Right", "Top" o "Bottom". Si la entrada de estilo es "por pestañas", la orientación de la entrada puede "izquierda" o "Right" y especifica dónde se agrega la pestaña. Si la entrada de estilo es "Flotar", la ventana de herramientas flota en primer lugar. Cuando se hace doble clic en la barra de título, las entradas de orientación y la ventana se aplican y la ventana usa el estilo de "por pestañas". Si la entrada de estilo es "AlwaysFloat", no se puede acoplar la ventana de herramientas. Si la entrada de estilo es "MDI", la ventana de herramientas está vinculada al área de MDI y se omite la entrada de la ventana.  
  
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
  
## <a name="tool-window-visibility"></a>Visibilidad de la ventana de herramienta  
 Valores de la subclave de visibilidad opcional determinan los valores de visibilidad de una ventana de herramienta. Los nombres de los valores se utilizan para almacenar los GUID de comandos que requieran la visibilidad de la ventana. Si se ejecuta el comando, el IDE garantiza que se crea y se hace visible la ventana de herramientas.  
  
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
  
|Nombre|Tipo|Datos|Descripción|  
|----------|----------|----------|-----------------|  
|(Predeterminado)|REG_SZ|Ninguna|Deje en blanco.|  
|*\< GUID>*|REG_DWORD o REG_SZ|0 o una cadena descriptiva.|Opcional. El nombre del elemento debe ser el GUID de un comando que requieren visibilidad. El valor contiene solo una cadena de carácter informativo. Normalmente, el valor es un `reg_dword` establecido en 0.|  
  
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
  
## <a name="see-also"></a>Vea también  
 [Elementos fundamentales de VSPackage](../misc/vspackage-essentials.md)