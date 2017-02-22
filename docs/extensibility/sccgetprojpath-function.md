---
title: "SccGetProjPath (funci&#243;n) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SccGetProjPath"
helpviewer_keywords: 
  - "SccGetProjPath (función)"
ms.assetid: 1079847e-d45f-4cb8-9d92-1e01ce5d08f6
caps.latest.revision: 15
caps.handback.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
---
# SccGetProjPath (funci&#243;n)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Esta función pide al usuario una ruta de acceso del proyecto, que es una cadena que solo es significativa para el complemento de control de código fuente. Se llama cuando el usuario es:  
  
-   Crear un nuevo proyecto  
  
-   Agregar un proyecto existente al control de versiones  
  
-   Intenta encontrar un proyecto existente de control de versión  
  
## Sintaxis  
  
```cpp#  
SCCRTN SccGetProjPath (  
   LPVOID pvContext,  
   HWND   hWnd,  
   LPSTR  lpUser,  
   LPSTR  lpProjName,  
   LPSTR  lpLocalPath,  
   LPSTR  lpAuxProjPath,  
   BOOL   bAllowChangePath,  
   LPBOOL pbNew  
);  
```  
  
#### Parámetros  
 pvContext  
 \[in\] La estructura de contexto complemento de control de código fuente.  
  
 hWnd  
 \[in\] Identificador de la ventana del IDE que se puede usar el complemento de control de código fuente como elemento primario para los cuadros de diálogo que proporciona.  
  
 lpUser  
 \[entrada, salida\] El nombre de usuario \(no superar SCC\_USER\_SIZE, incluido el terminador NULL\)  
  
 lpProjName  
 \[entrada, salida\] El nombre del proyecto IDE, área de trabajo del proyecto o archivo MAKE \(no superar SCC\_PRJPATH\_SIZE, incluido el terminador NULL\).  
  
 lpLocalPath  
 \[entrada, salida\] Ruta de trabajo del proyecto. Si `bAllowChangePath` es `TRUE`, el complemento de control de código fuente puede modificar esta cadena \(no superar \_MAX\_PATH, incluido el terminador null\).  
  
 lpAuxProjPath  
 \[entrada, salida\] Un búfer de la ruta de acceso devuelta del proyecto \(no superar SCC\_PRJPATH\_SIZE, incluido el terminador NULL\).  
  
 bAllowChangePath  
 \[in\] Si es `TRUE`, el complemento de control de código fuente puede solicitar y modificar el `lpLocalPath` cadena.  
  
 pbNew  
 \[entrada, salida\] Que entran en el valor indica si se debe crear un nuevo proyecto. El valor devuelto indica el éxito de la creación de un proyecto:  
  
|Entrante|Interpretación|  
|--------------|--------------------|  
|TRUE|El usuario puede crear un nuevo proyecto.|  
|FALSE|El usuario no puede crear un nuevo proyecto.|  
  
|Saliente|Interpretación|  
|--------------|--------------------|  
|TRUE|Se crea un nuevo proyecto.|  
|FALSE|Se ha seleccionado un proyecto existente.|  
  
## Valor devuelto  
 La implementación de complemento del control de origen de esta función debe devolver uno de los siguientes valores:  
  
|Valor|Descripción|  
|-----------|-----------------|  
|SCC\_OK|El proyecto se creó o se recuperó correctamente.|  
|SCC\_I\_OPERATIONCANCELED|Se canceló la operación.|  
|SCC\_E\_ACCESSFAILURE|Hubo un problema al obtener acceso al sistema de control de origen, probablemente debido a problemas de red o de contención.|  
|SCC\_E\_CONNECTIONFAILURE|Hubo un problema al intentar conectar con el sistema de control de código fuente.|  
|SCC\_E\_NONSPECIFICERROR|Se produjo un error no especificado.|  
  
## Comentarios  
 El propósito de esta función es para que el IDE adquirir los parámetros `lpProjName` y `lpAuxProjPath`. Después de que el complemento de control de código fuente pide al usuario esta información, transfiere estos dos cadenas a IDE. El IDE conserva estas cadenas en el archivo de solución y los pasa a la [SccOpenProject](../extensibility/sccopenproject-function.md) cada vez que el usuario abre este proyecto. Estas cadenas de habiliten el complemento registrar la información asociada a un proyecto.  
  
 Cuando la función se llama por primera vez, `lpAuxProjPath` se establece en una cadena vacía.`lProjName` También puede estar vacío, o puede contener el nombre de proyecto IDE, que puede usar u omitir el complemento de control de código fuente. Cuando la función vuelve correctamente, el complemento devuelve las dos cadenas correspondientes. El IDE no realiza suposiciones sobre estas cadenas, no los utilizará y no permitirá al usuario modificarlos. Si el usuario desea cambiar la configuración, el IDE llamará `SccGetProjPath` nuevo, pasando los mismos valores había recibido anteriormente. Esto proporciona el complemento control completo sobre estas dos cadenas.  
  
 Para `lpUser`, el IDE puede pasar un nombre de usuario o simplemente puede pasar un puntero a una cadena vacía. Si hay un nombre de usuario, el complemento de control de código fuente debe usar como valor predeterminado. Sin embargo, si se ha pasado ningún nombre o error de inicio de sesión con el nombre especificado, el complemento debe solicitar al usuario para un inicio de sesión y pase el nombre nuevo en `lpUser` cuando recibe un inicio de sesión válido. Dado que el complemento puede cambiar esta cadena, el IDE siempre asignará un búfer de tamaño \(`SCC_USER_LEN`\+ 1\).  
  
> [!NOTE]
>  La primera acción que realiza el IDE puede ser una llamada a la `SccOpenProject` \(función\) o `SccGetProjPath` \(función\). Por lo tanto, ambas tienen idéntica `lpUser` parámetro, que permite el control de código fuente complemento al usuario en sesión en cualquier momento. Incluso si el valor devuelto de la función indica un error, el complemento debe rellenar esta cadena con un nombre de inicio de sesión válido.  
  
 `lpLocalPath` es el directorio donde el usuario guarda el proyecto. Puede ser una cadena vacía. Si no hay ningún directorio definido actualmente \(como en el caso de un usuario intenta descargar un proyecto desde el sistema de control de código fuente\) y si `bAllowChangePath` es `TRUE`, el complemento de control de código fuente puede preguntar al usuario para la entrada o utilizar algún otro método para colocar su propia cadena en `lpLocalPath`. Si `bAllowChangePath` es `FALSE`, el complemento no debería cambiar la cadena, porque el usuario ya está trabajando en el directorio especificado.  
  
 Si el usuario crea un nuevo proyecto a colocarse bajo control de código fuente, el complemento de control de código fuente podría no realmente crearlo en el sistema de control de código fuente en el momento `SccGetProjPath` se llama. En su lugar, devuelve la cadena junto con un valor distinto de cero para `pbNew`, que indica que el proyecto se creará en el sistema de control de código fuente.  
  
 Por ejemplo, si un usuario en el **nuevo proyecto** asistente en Visual Studio agrega su proyecto al control de código fuente, Visual Studio llama a esta función y el complemento determina si es correcto crear un nuevo proyecto en el sistema de control de código fuente que contiene el proyecto de Visual Studio. Si el usuario hace clic **Cancelar** antes de completar el asistente, nunca se crea el proyecto. Si el usuario hace clic **Aceptar**, Visual Studio llama a `SccOpenProject`, pasando `SCC_OPT_CREATEIFNEW`, y se crea el proyecto de control de código fuente en ese momento.  
  
## Vea también  
 [Funciones de API de complemento de Control de código fuente](../extensibility/source-control-plug-in-api-functions.md)   
 [SccOpenProject](../extensibility/sccopenproject-function.md)