# API-Prestaciones

// calcule las prestaciones de un empleado de acuerdo a las reglas establecidas en el Ministerio de Trabajo de República Dominicana

// El programa tendrá las siguientes entradas:

// 1. Nombre de la persona
//1.1 cedula
// 2. Salario Mensual
// 2.1 el salario mensual se divide 23.83 entre el salario mensual
// 2.2 el salario quincenal se divide 11.91 entre el salario quincenal
// 2.3 el salario semanal se divide 5.5 entre el salario semanal 
//2.4 cuanto ganaba mensual (10,000)
// 3. Cantidad de años, meses y días laborando
// 4. Si ha sido preavisado
//4.1 si el salario mensual son RD$420 son 28 dias de preavisado y luego se multiplica 
//
// 5. Si hay que incluir cesantía
// 3 meses laborando = 6 dias de cesantia 
//. 6 meses laborando = 13 dias de cesantia
// 1 año laborando - 21 dia de cesantia 
// 5 años laborando =  23 dias de censantia 
// si son 7 años laborando se multiplica por 23, el resultado de la multiplicacion por el salario RD$420 x 161 dias de censantia
// 
// 6. Si ha tomado vacaciones en el último año
// 1 año laborando = 14 dias x RD$420 
// 5 años laborando = 18 dias de salario 
// si son 18 dias se multiplica por el salario RD$420 
//
// 7. Si incluye el salario de navidad
// se obtiene todo lo que gano en el año laborando y luego se divide entre 12 
// 10,000 x 5 meses son 50,000
// y 50,000 dividido entre 12 

// Luego de realizar los diferentes cálculos, la salida del programa debe ser imprimir los siguientes valores:

// 1. Monto del Preaviso
// 2. Monto de la Cesantía
// 3. Monto de las Vacaciones
// 4. Monto del Salario de Navidad
// 5. Monto total a recibir


type Person ={
    name: string 
    nationality : string 
    age : number
    sex : string 
    dateIn: Date;
    dateOut: Date; 
    salary: number; 
    paymentFrecuency: "Anual"|"Mensual"|"Diario"
    foreWarnedPay: boolean;
    unemployment: boolean;
    vacation: boolean;
    christmasPay: boolean;

 }

const customer: Person ={

    name: "Raysell",
    nationality: "Dominicano",
    age: 23, 
    sex: "masculino",
    dateIn: new Date ("23/7/2020"),
    dateOut: new Date ("22/7/2040"),
    salary: 60000,
    paymentFrecuency:"Mensual",
    foreWarnedPay: true,
    unemployment: true,
    vacation: true, 
    christmasPay: true,

}
const Day = 1000 * 60 * 60 * 24;
const timeWorking = customer.dateOut.getTime() - customer.dateIn.getTime();
const workingTimeDays = timeWorking / Day;
const workingOnMonths =  workingTimeDays / 30.47;


console.log(customer.name)
console.log("time working" + workingTimeDays)

  
    

const calculateBenefits = () =>{


const dailySalary:number = Number ((customer.salary /23.83).toFixed(2));
console.log ("daily salary " + dailySalary)
let foreWarnedPay: number = 0;
    let unemployment: number = 0;
    let vacationPay: number = 0;
    let christmasPay: number = 0;

 

    if (workingOnMonths >= 3 && workingOnMonths <= 6){

    foreWarnedPay = dailySalary * 7;
    }
    
    else if (workingOnMonths >= 6 && workingOnMonths <= 12){
    const forWarnedPay = dailySalary * 14;
    }
    
    else if (workingOnMonths > 12)
    { foreWarnedPay = dailySalary * 28;
   
    }
     console.log("Monto de Preaviso" + " " + foreWarnedPay);
    if (customer.unemployment){
    if (workingOnMonths >=3 && workingOnMonths <=6){
        unemployment = dailySalary * 7;

    }else if (workingOnMonths >= 6 && workingOnMonths <=12){
        unemployment = dailySalary * 13;


    }else if (workingTimeDays >=60){
        unemployment = workingOnMonths / 12 * 23 * dailySalary ;

    }
    console.log("monto de censantia " + unemployment);
    }
if (customer.vacation){
    if (workingTimeDays >=5 && workingTimeDays <=12){
        vacationPay = dailySalary * 6;

    }else if (workingTimeDays >= 12 && workingTimeDays <=60){
        vacationPay = dailySalary * 14;


    }else if (workingTimeDays >=60){
        vacationPay =  dailySalary * 18;

    }
    console.log("monto de vacaciones " + vacationPay);
    }
    if (customer.christmasPay){
    if (workingOnMonths >=3 && workingOnMonths <=6){
        christmasPay = dailySalary * 7;

    }else if (workingOnMonths >= 6 && workingOnMonths <=12){
        christmasPay = dailySalary * 13;


    }else if (workingOnMonths >=60){
        christmasPay = workingOnMonths / 12 * 23 * dailySalary ;

    }
    console.log("monto de navidad " + christmasPay);
    }
}
    calculateBenefits()
