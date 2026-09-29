------------------------------------------------------------------------

# Especificación de requisitos

**Sistema:** SubTrack  
**Autor:** Omar Enrique Buenrostro Islas  
**Versión:** 1.0  
**Fecha de la última actualización:** 28 de septiembre de 2026


------------------------------------------------------------------------

**Propósito del documento:**

Este documento define los requisitos funcionales y no funcionales de SubTrack. Su propósito es establecer de manera clara y verificable las funciones, restricciones y atributos de calidad que deberá cumplir el sistema durante su desarrollo.

**Alcance del sistema:**

SubTrack permitirá a los usuarios registrar y administrar sus suscripciones en un solo lugar. El sistema permitirá consultar próximos cobros, conocer los gastos relacionados con suscripciones y generar recordatorios.

El sistema incluirá:

- Registro y administración de suscripciones.
- Registro de costo, frecuencia de pago y fecha del próximo cobro.
- Consulta de próximos cobros.
- Cálculo del gasto total mensual y anual en suscripciones.
- Recordatorios configurables de próximos cobros.
- Administración de servicios y categorías.
- Control de acceso a la información de cada usuario.

**Fuera del alcance:**

- Realizar pagos desde SubTrack.
- Cancelar directamente una suscripción con un proveedor externo.
- Acceder a cuentas bancarias del usuario.
- Detectar automáticamente cargos bancarios.
- Contratar servicios externos desde SubTrack.
- Realizar reembolsos.
- Administrar métodos de pago reales.
- Conservar suscripciones canceladas dentro del historial de suscripciones activas.

El acceso a cuentas bancarias y la realización de pagos quedan fuera del alcance porque SubTrack tiene como objetivo organizar y dar seguimiento a las suscripciones, no funcionar como una aplicación bancaria.



------------------------------------------------------------------------

## 2. Usuarios y su contexto

| Usuario | Qué hace hoy sin el sistema | Qué espera del sistema |
|---|---|---|
| **Usuario** | Revisa diferentes aplicaciones, correos o movimientos de su tarjeta para conocer cuánto está gastando y cuándo será el siguiente cobro. | Tener sus suscripciones organizadas en un solo lugar, consultar sus próximos cobros, elegir cuándo recibir recordatorios y conocer su gasto total mensual y anual. |
| **Administrador** | La información general de servicios y categorías debe mantenerse organizada por separado. | Mantener organizada y actualizada la información general utilizada por SubTrack. |

### Contexto identificado durante la entrevista

La entrevista permitió confirmar que el usuario necesita controlar sus suscripciones sin tener que consultar diferentes aplicaciones, correos o movimientos bancarios.

También se confirmó que el usuario quiere elegir con cuánta anticipación recibir un recordatorio y considera suficientes el nombre, costo, frecuencia y próximo cobro para registrar una suscripción.

Durante la entrevista se identificó que el usuario no desea conservar las suscripciones canceladas en el historial porque podrían confundirse con las suscripciones que siguen activas.

Además, surgió la necesidad de mostrar cuánto dinero se gastó en total durante el mes y contemplar también el gasto anual.

### Conflictos identificados entre usuarios

El usuario necesita libertad para registrar y modificar sus propias suscripciones, mientras que el administrador necesita mantener controlada y organizada la información general del sistema.

Por esta razón, cada usuario tendrá control sobre sus propias suscripciones y el administrador tendrá permisos para gestionar la información general de servicios y categorías.



------------------------------------------------------------------------

## 3. Requisitos funcionales

### 3.1 Resumen

  ID       Nombre   Prioridad   Origen
  -------- -------- ----------- --------
  RF-001                        
  RF-002                        
  RF-003                        

### 3.2 Fichas

*Una ficha por requisito, con los mismos campos siempre. Abajo va un
ejemplo completo; bórralo cuando escribas los tuyos.*

#### RF-001 · Registro de consulta

  -----------------------------------------------------------------------
  Campo                                                Contenido
  ---------------------------------------------------- ------------------
  **Descripción**                                      El sistema
                                                       registra la
                                                       consulta de un
                                                       paciente con
                                                       fecha, motivo,
                                                       diagnóstico y
                                                       veterinario que
                                                       atendió.

  **Origen**                                           Entrevista con el
                                                       veterinario, 15 de
                                                       septiembre.

  **Prioridad**                                        Imprescindible

  **Criterio de aceptación**                           Al guardar una
                                                       consulta con los
                                                       cuatro datos, esta
                                                       aparece en el
                                                       historial del
                                                       paciente con la
                                                       fecha correcta. Si
                                                       falta alguno, el
                                                       sistema no guarda
                                                       y señala cuál
                                                       falta.

  **Relacionado con**                                  RF-004,
                                                       RNF-SEG-001
  -----------------------------------------------------------------------

#### RF-002 ·

  Campo                        Contenido
  ---------------------------- -----------
  **Descripción**              
  **Origen**                   
  **Prioridad**                
  **Criterio de aceptación**   
  **Relacionado con**          

------------------------------------------------------------------------

## 4. Requisitos no funcionales

### 4.1 Resumen

  ID            Atributo      Nombre   Prioridad   Origen
  ------------- ------------- -------- ----------- --------
  RNF-REN-001   Rendimiento                        
  RNF-SEG-001   Seguridad                          
  RNF-USA-001   Usabilidad                         

### 4.2 Fichas

*Agrupadas por atributo de calidad. Abajo va un ejemplo completo;
bórralo cuando escribas los tuyos.*

#### RNF-REN-001 · Tiempo de consulta del historial

  -----------------------------------------------------------------------
  Campo                                               Contenido
  --------------------------------------------------- -------------------
  **Atributo de calidad**                             Rendimiento

  **Descripción**                                     El historial
                                                      completo de un
                                                      paciente se
                                                      despliega en menos
                                                      de tres segundos.

  **Métrica**                                         Tiempo entre la
                                                      solicitud y el
                                                      despliegue
                                                      completo, medido
                                                      con hasta 500
                                                      consultas
                                                      registradas para
                                                      ese paciente.

  **Origen**                                          Derivado del tipo
                                                      de sistema: de
                                                      información, con
                                                      consulta frecuente
                                                      durante la
                                                      atención.

  **Prioridad**                                       Imprescindible

  **Por qué importa**                                 La consulta ocurre
                                                      con el paciente
                                                      enfrente. Si tarda,
                                                      el veterinario
                                                      abandona el sistema
                                                      y vuelve al
                                                      expediente en
                                                      papel.

  **Afecta a**                                        RF-001, RF-004
  -----------------------------------------------------------------------

#### RNF-SEG-001 ·

  Campo                     Contenido
  ------------------------- -----------
  **Atributo de calidad**   
  **Descripción**           
  **Métrica**               
  **Origen**                
  **Prioridad**             
  **Por qué importa**       
  **Afecta a**              

------------------------------------------------------------------------

## 5. Casos de uso

*Se trabajan en la semana 7, después de la entrevista. Cada caso de uso
se relaciona con los requisitos funcionales que realiza.*

------------------------------------------------------------------------

## 6. Trazabilidad

*Esta tabla es la que hace posible el análisis de impacto de la semana
15. Mantenla actualizada conforme cambien los requisitos.*

  --------------------------------------------------------------------------
  Requisito   Origen           Caso de uso             Elemento del
                                                       prototipo
  ----------- ---------------- ----------------------- ---------------------
  RF-001      Entrevista 15    CU-01 Registrar         Pantalla de consulta
              sep              consulta                

                                                       
  --------------------------------------------------------------------------

------------------------------------------------------------------------

## 7. Registro de cambios

*Cada modificación posterior a la primera versión se anota aquí. Un
requisito eliminado se marca como tal, pero su identificador no se
reutiliza.*

  Fecha   Requisito   Qué cambió   Por qué
  ------- ----------- ------------ ---------
                                   

------------------------------------------------------------------------

## Antes de entregar

-   [ ] Todos los requisitos tienen identificador único y ninguno está
    repetido
-   [ ] Cada requisito expresa una sola idea
-   [ ] Cada requisito funcional tiene criterio de aceptación
    comprobable
-   [ ] Cada requisito no funcional tiene una métrica, no solo un
    adjetivo
-   [ ] El campo Origen distingue lo confirmado por el cliente de lo que
    sigo suponiendo
-   [ ] Hay al menos un requisito no funcional por cada atributo de
    calidad que impone mi tipo de sistema
-   [ ] Ningún requisito impone una solución técnica
-   [ ] Todos los requisitos caben dentro del alcance declarado
-   [ ] La tabla de trazabilidad está completa
-   [ ] Mi dupla revisó el documento y su revisión está registrada
-   [ ] Borré los ejemplos y las instrucciones en cursiva
