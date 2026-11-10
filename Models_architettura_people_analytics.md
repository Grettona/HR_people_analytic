#Architettura de proceso y datos - People Analytics

#Offboarding(flujo de captura de datos)
```mermaid
flowchart TD
  A[Empleado presenta renuncia] -> B[HR registra fecha y motivo de salida]
  B -> C[Envio de encuesta Exit interview]
  C -> D{Encuesta completada?}
  D -> Sì -> E[Guardar respuestas en base de datos HR]
  D -> No -> F[Recordatorio automatico a los 3 dias]
  F -> E
  E -> G[Calculo de KPI de rotacion en R]
```

#Modelo entità-relazione (struttura dei dati)
```mermaid
erDiagram
  EMPLEADOS ||--o{EVALUACIONES : recibe
  EMPLEADOS ||--o| SALIDAS : registra

  EMPLEADOS {
    int id_employee PK
    string department
    string Job_title
    decimal salary_annual
}
EVALUACIONES  {
    int id_evaluation PK
    int id_empleado FK
    int performance_score
}
SALIDAS {
    int id_salida PK
    int id_employee FK
    string termination_reasson
}
```
