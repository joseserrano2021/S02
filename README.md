# S02
Sistemas operativos 2

repositorio practivo

este camio se hice por pc 
#
Integrantes:

Ramos Escandon Gilberto Gustavo

Serrano Torredo Jose Luis

Rincon Lopez Abraham

Rico Garcia Octaviano

Martinez de Leon  Raul Alejandro

Gomez Vazques Francisco Javier

//Clase mein
    public static void main(String[] args){
        PCB proceso=new PCB(1,"proceso",1,0,1024,0,5);
        proceso.setTiempoproceso(6);
        PCB proceso1=new PCB(2,"proceso1",1,0,1024,0,5);
        
        proceso1.setTiempoproceso(7);
        
    System.out.println("id:"+ proceso.getPid());
    Cola ready =new Cola(true);
    Cola ejecucion=new Cola(false);
    
    
    ready.enqueve(proceso);
    ready.enqueve(proceso1);
    
    //remover de ready -> ejecucion

    
    PCB t=ready.dequeve();
    while(t!=null){
        System.out.println("r->e:"+ t.getNombre());
    ejecucion.enqueve(t);
    
    //remover de ejecucion -> ready; reducir el tiempo
    
    PCB e = ejecucion.dequeve();
    e.setTiempoproceso(e.getTiempoproceso()-1);//ejecutado  10
    System.out.println("tiempoproceso:"+ e.getNombre());
    if(e.getTiempoproceso()>0){
        System.out.println("e->r:"+ e.getNombre());
        ready.enqueve(e);
    }else{
        System.out.println("--FIN--"+ e.getNombre());
    }
    t=ready.dequeve();
    }
    
    }
    
    //Clase cola
     private ArrayList<PCB> datos;
   private boolean ordenar=false;
    
    public Cola(boolean ordenar){
        this.datos=new ArrayList<>();
        this.ordenar=ordenar;
    }
    //metodo para agregar
    //1 el proceso se acaba
    //0 el prceso no se acaba
   public int enqueve(PCB p){
      this.datos.add(p);
      if(ordenar)
      Collections.sort(datos);
      return 1;
    }
    
    //metodo para remover
   public  PCB dequeve(){
        if(this.datos.size()>=1){
            if(ordenar)
                Collections.sort(datos);
         return this.datos.remove(0);   
        }
       
        return null;
    }
    
    //metodo para recuperar los elementos
    @Override
    public String toString(){
        //for (int i=0;i<datos.size();i++)
        //for (PCB p:this.datos)
        //StringBuilder
        String s="";
      for(PCB p:this.datos){
          s=s+p;
      }
      return s;
    }
    
    //clase PCB
    
       private int pid;
   private String nombre;
   private int estado;
   private int membase;
   private int tiempoproceso;

   private int memlimite;
   private int contador; //direccion de memoria de la instruccion
   private int prioridad;
    
    public PCB(int pid,String nombre,int estado,int membase,int memlimite, int contador, int prioridad){
       
        this.pid=pid;
        this.nombre=nombre;
        this.estado=estado;
        this.membase=membase;
        this.memlimite=memlimite;
        this.contador=contador;
        this.prioridad=prioridad;
    }

    public int getPid() {
        return pid;
    }

    public void setPid(int pid) {
        this.pid = pid;
    }

    public String getNombre() {
        return nombre;
    }

    public void setNombre(String nombre) {
        this.nombre = nombre;
    }

    public int getEstado() {
        return estado;
    }

    public void setEstado(int estado) {
        this.estado = estado;
    }

    public int getMembase() {
        return membase;
    }

    public void setMembase(int membase) {
        this.membase = membase;
    }

    public int getMemlimite() {
        return memlimite;
    }

    public void setMemlimite(int memlimite) {
        this.memlimite = memlimite;
    }

    public int getContador() {
        return contador;
    }

    public void setContador(int contador) {
        this.contador = contador;
    }

    public int getPrioridad() {
        return prioridad;
    }

    public void setPrioridad(int prioridad) {
        this.prioridad = prioridad;
    }
    
        public int getTiempoproceso() {
        return tiempoproceso;
    }

    public void setTiempoproceso(int tiempoproceso) {
        this.tiempoproceso = tiempoproceso;
    }
    
    @Override
    public String toString(){
        return "PCB{"+
                "pid= "+ pid+
                ", nombre=" + nombre+'\"'+
                "]";
    }
    
    /*respuesta
    o iguales
    >0 mayor
    <0 menor
    */
    @Override
    public int compareTo(PCB pcb){
        return this.tiempoproceso - pcb.tiempoproceso;
    }
    


# :D
