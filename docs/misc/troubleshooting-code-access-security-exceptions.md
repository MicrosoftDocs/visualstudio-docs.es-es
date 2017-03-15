---
title: "Soluci&#243;n de problemas de excepciones de seguridad de acceso del c&#243;digo | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "CodeAccessPermission (clase)"
  - "CodeAccessSecurityException (clase)"
  - "seguridad de acceso del código, solución de problemas"
  - "seguridad [depurador], solución de problemas de seguridad de acceso del código"
  - "solución de problemas de seguridad de acceso del código"
ms.assetid: ca368d3b-f6d0-4c89-af59-d94f343fca35
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Soluci&#243;n de problemas de excepciones de seguridad de acceso del c&#243;digo
Los permisos controlan las acciones que el código puede o no realizar. Cuando se ejecuta una aplicación, el runtime le concede un conjunto de permisos. Si los permisos son suficientes, se ejecuta correctamente; de lo contrario se produce una excepción de seguridad.  
  
 Los permisos concedidos al código están determinados por la ubicación desde la que se inicia la aplicación \(por ejemplo, Internet, intranet o el equipo local\) y las configuraciones de seguridad del equipo en el que la aplicación se está ejecutando. Puesto que esta configuración puede variar de un equipo a otro, no siempre es posible anticipar si el código recibirá los permisos necesarios.  
  
 La solicitud de permisos garantiza que el código se ejecute si la directiva de seguridad del equipo local lo permite. Si no se solicitan los permisos necesarios, se corre el riesgo de que el código no se ejecute. Para más información sobre los permisos de acceso del código y sobre cómo solicitarlos, vea [Permisos de acceso del código](http://msdn.microsoft.com/es-es/e5ae402f-6dda-4732-bbe8-77296630f675) o [NIB: Solicitud de permisos](http://msdn.microsoft.com/es-es/0447c49d-8cba-45e4-862c-ff0b59bebdc2). Para más información sobre los bloques `Try...Catch`, vea [Try...Catch...Finally \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/try-catch-finally-statement).  
  
 Las aplicaciones [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] pueden solicitar permisos adicionales, si es necesario, en la página de seguridad del Diseñador de aplicaciones. Para obtener más información, consulta [Cómo: Establecer permisos personalizados para una aplicación ClickOnce](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md).  
  
 Entre las posibles causas de las excepciones de seguridad de acceso del código se incluyen:  
  
-   **Portapapeles.** Pegar del Portapapeles mediante programación es una característica restringida del código administrado, porque el Portapapeles puede contener información confidencial.  
  
-   **Acceso al Registro o al sistema de archivos.** El acceso al sistema de archivos local está restringido. Si tiene acceso a un archivo o recurso que se implementa con su ensamblado, utilice el código `Assembly.GetExecutingAssembly.Location` para obtener la ruta al ensamblado.  
  
-   **Acceso a la red.** Asegúrese de que el ensamblado utiliza el mismo protocolo con el que se cargó. Generalmente, sólo se permite la comunicación por red con la dirección URL de origen del ensamblado.  
  
-   **Impresión.** El software que se ejecuta en la zona Internet solo puede imprimir usando un cuadro de diálogo común. Está restringido al uso de la impresora predeterminada únicamente si utiliza un cuadro de diálogo común para permitir que el usuario seleccione una impresora.  
  
-   **Serialización.** La capacidad para recompilar un objeto a partir de datos arbitrarios se restringe al código ejecutado con plena confianza. Para la serialización XML, el tipo `XmlSerializer` debería poder utilizarse técnicamente por código de confianza parcial. Para más información sobre el tipo `XmlSerializer`, vea [XmlSerializer Class](https://msdn.microsoft.com/en-us/library/system.xml.serialization.xmlserializer.aspx).  
  
-   **Reflexión.** Muchas de las características relacionadas con la reflexión en tiempo de ejecución son de uso restringido por código de confianza parcial.  
  
## Comprobación del código para determinar si producirá una excepción de seguridad de acceso a código  
 Si tiene un bloque de código con la posibilidad de producir una excepción `CodeAccessSecurityException`, utilice un bloque `Try...Catch` para permitir que el código se ejecute, si es posible, y evitar el error, si no es posible.  
  
 A veces, deseará diseñar la aplicación para que ajuste su comportamiento a los permisos concedidos por el sistema host. Por ejemplo, puede que desee deshabilitar un comando Print en un menú si la aplicación no tiene permisos para imprimir.  
  
 Para comprobar esta situación, puede crear una instancia de una clase derivada de `CodeAccessPermission` como `FileIOPermission`. A continuación, puede ejecutar el método `Demand` en el permiso dentro de un bloque `Try...Catch`. Si se produce la excepción, el ensamblado no dispone de permiso.  
  
 En el siguiente ejemplo se prueba si el ensamblado tiene permiso de `EventLogPermission` ejecutando o creando un permiso `EventLogPermission` y ejecutando su método `Demand` dentro de un bloque `Try...Catch` para determinar si `Demand` es correcta.  
  
```  
Try Dim MyPermission As New EventLogPermission MyPermission.Demand() MsgBox(MyPermission.ToString()) Catch ex As Exception MsgBox("Assembly lacks EventLogPermission.") End Try  
```  
  
## Vea también  
 [Permisos de acceso a código](http://msdn.microsoft.com/es-es/e5ae402f-6dda-4732-bbe8-77296630f675)   
 [NIB: Solicitud de permisos](http://msdn.microsoft.com/es-es/0447c49d-8cba-45e4-862c-ff0b59bebdc2)   
 [Code Access Security Basics](../Topic/Code%20Access%20Security%20Basics.md)