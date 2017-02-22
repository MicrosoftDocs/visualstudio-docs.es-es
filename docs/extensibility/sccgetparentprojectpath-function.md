---
title: "SccGetParentProjectPath (funci&#243;n) | Microsoft Docs"
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
  - "SccGetParentProjectPath"
helpviewer_keywords: 
  - "SccGetParentProjectPath (función)"
ms.assetid: 62a71579-36b3-48b9-a1c8-04ab100efa08
caps.latest.revision: 17
caps.handback.revision: 17
ms.author: "gregvanl"
manager: "ghogen"
---
# SccGetParentProjectPath (funci&#243;n)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Esta función determina la ruta de acceso del proyecto principal de un proyecto especificado. Esta función se invoca cuando el usuario agrega un proyecto de Visual Studio para el control de código fuente.  
  
## Sintaxis  
  
```cpp#  
SCCRTN SccGetParentProjectPath(  
   LPVOID pContext,  
   HWND   hWnd,  
   LPSTR  lpUser,  
   LPCSTR lpProjPath,  
   LPSTR  lpAuxProjPath,  
   LPSTR  lpParentProjPath  
);  
```  
  
#### Parámetros  
 pContext  
 \[in\] El puntero de contexto de complemento de control de código fuente.  
  
 hWnd  
 \[in\] Identificador de la ventana del IDE que se puede usar el complemento de control de código fuente como elemento primario para los cuadros de diálogo que proporciona.  
  
 lpUser  
 \[entrada, salida\] El nombre de usuario \(hasta SCC\_USER\_SIZE, incluido el terminador NULL\).  
  
 lpProjPath  
 \[in\] Cadena que identifica la ruta de acceso del proyecto \(hasta SCC\_PRJPATH\_SIZE, incluido el terminador NULL\).  
  
 lpAuxProjPath  
 \[entrada, salida\] Cadena auxiliar que identifica el proyecto \(hasta SCC\_PRJPATH\_SIZE, incluido el terminador NULL\).  
  
 lpParentProjPath  
 \[entrada, salida\] Cadena de salida que identifica la ruta de acceso del proyecto principal \(hasta SCC\_PRJPATH\_SIZE, incluido el terminador NULL\).  
  
## Valor devuelto  
 La implementación de complemento del control de origen de esta función debe devolver uno de los siguientes valores:  
  
|Valor|Descripción|  
|-----------|-----------------|  
|SCC\_OK|Ruta de acceso del proyecto principal se obtuvo correctamente.|  
|SCC\_E\_INITIALIZEFAILED|No se pudo inicializar el proyecto.|  
|SCC\_E\_INVALIDUSER|No se pudo iniciar el usuario el complemento de control de código fuente.|  
|SCC\_E\_UNKNOWNPROJECT|Proyecto es desconocido para el complemento de control de código fuente.|  
|SCC\_E\_INVALIDFILEPATH|Ruta de acceso de archivo no válido o no utilizable.|  
|SCC\_E\_NOTAUTHORIZED|El usuario no puede realizar esta operación.|  
|SCC\_E\_ACCESSFAILURE|Hubo un problema al obtener acceso al sistema de control de origen, probablemente debido a problemas de red o de contención. Se recomienda un reintento.|  
|SCC\_E\_PROJSYNTAXERR|Sintaxis de proyecto no válida.|  
|SCC\_E\_CONNECTIONFAILURE|Problema de conexión de almacén.|  
|SCC\_E\_NONSPECIFICERROR<br /><br /> SCC\_E\_UNKNOWNERROR|Error no específico.|  
  
## Comentarios  
 Esta función devuelve un código de éxito o error y, si es correcto, rellena la variable `lpParentProjPath` con la ruta de acceso completa del proyecto al proyecto especificado.  
  
 Esta función devuelve al elemento primario de ruta de acceso del proyecto de un proyecto existente. Para el proyecto raíz, la función devuelve la ruta de acceso del proyecto que se pasó en \(es decir, el mismo proyecto ruta de acceso raíz\). Tenga en cuenta que la ruta de acceso de un proyecto es una cadena que solo es significativa para el complemento de control de código fuente.  
  
 El IDE está preparado para aceptar los cambios en el `lpUser` y `lpAuxProjPath` también parámetros. El IDE se conservar estas cadenas y pasarlos a la [SccOpenProject](../extensibility/sccopenproject-function.md) cuando el usuario abre este proyecto en el futuro. Estas cadenas, por lo tanto, proporcionan un método para la información de seguimiento que se debe asociar a un proyecto de complemento de control de código fuente.  
  
 Esta función es similar a la [SccGetProjPath](../extensibility/sccgetprojpath-function.md), salvo que no solicita al usuario que seleccione un proyecto. Nunca se crea un nuevo proyecto pero funciona sólo con un proyecto existente.  
  
 Cuando `SccGetParentProjectPath` se llama, `lpProjPath` y `lpAuxProjPath` no estarán vacíos y corresponderá a un proyecto válido. Estas cadenas se reciben normalmente por el IDE desde una llamada anterior a la `SccGetProjPath` \(función\).  
  
 El `lpUser` argumento es el nombre de usuario. El IDE se pasará en el mismo nombre de usuario que anteriormente había recibido de la `SccGetProjPath` \(función\) y el complemento de control de código fuente, deben usar el nombre de forma predeterminada. Si el usuario ya tiene una conexión abierta con el complemento, a continuación, el complemento debe intentar eliminar las peticiones para asegurarse de que funciona en modo silencioso. Sin embargo, si se produce un error en el inicio de sesión, el complemento debe solicitar al usuario para un inicio de sesión y, cuando recibe un inicio de sesión válido, pase el nombre nuevo en `lpUser`. Dado que el complemento puede cambiar esta cadena, el IDE siempre asignará un búfer de tamaño \(`SCC_USER_LEN`\+ 1\). Si se cambia la cadena, la nueva cadena debe ser un nombre de inicio de sesión válido \(al menos tan válido como la cadena anterior\).  
  
## Notas técnicas de SccCreateSubProject y SccGetParentProjectPath  
 Agregar soluciones y proyectos al control de código fuente se ha simplificado en Visual Studio para minimizar el número de veces que un usuario debe seleccionar las ubicaciones en el sistema de control de código fuente. Estos cambios se activan mediante Visual Studio si un complemento de control de código fuente admite tanto de las nuevas funciones, la [SccCreateSubProject](../extensibility/scccreatesubproject-function.md) y la `SccGetParentProjectPath` \(función\). Sin embargo, puede utilizarse la entrada de registro siguiente para deshabilitar estos cambios y revertir al comportamiento anterior de Visual Studio \(origen de Control de complemento de API versión 1.1\):  
  
 \[HKEY\_CURRENT\_USER\\Software\\Microsoft\\VisualStudio\\8.0\\SourceControl\] "DoNotCreateSolutionRootFolderInSourceControl" \= dword: 00000001  
  
 Si esta entrada del registro no existe o está establecida en DWORD: 00000000, Visual Studio intenta usar las nuevas funciones, `SccCreateSubProject`y`SccGetParentProjectPath`.  
  
 Si la entrada del registro se establece en DWORD: 00000001, Visual Studio no intenta utilizar estas funciones nuevas y las operaciones de agregar al control de código fuente funcionan como lo hacían en versiones anteriores de Visual Studio.  
  
## Vea también  
 [Funciones de API de complemento de Control de código fuente](../extensibility/source-control-plug-in-api-functions.md)   
 [SccCreateSubProject](../extensibility/scccreatesubproject-function.md)   
 [SccGetProjPath](../extensibility/sccgetprojpath-function.md)