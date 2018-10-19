# Was ist neu in Java 10?

## Local Variable Type Inference

    String message = "Hello Java 10";

Variablen lassen sich lokal mittels var deklarieren
    public void localUseOfVar(){
        var message = "Hello Java 10";
        assertThat(message instanceof String).isTrue();
    }

Das geht nur in lokalem Kontext mit Initialisierung!
### Verboten
    public var message = ""; // won't compile: only allowewd in local contexts!
    var illegal1; // won't compile : requires an initializer!
    var illegal2 = null; // won't compile : initializer is null!
    var lambda = (String s)-> System.out.println(s);
    // won't compile: var is not allowed with lambda expressions!
    var array = {1,2,3,4};     // won't compile: var ist not allowed for array
                               // initializer expressions!
### lass ma'lieber:
    var result = service.doSomething(); // unklar
    var list = new ArrayList<>();       // => ArrayList<Object>

    // blöd zu lesende lambdas:
    var dingens = personFinder.find(name).map(Person::getAddress).orElse(new Address("",""));

###  var ist kein keyword!
    private String var = "var is not a keyword!";
    
    public void var() {
        var var = this.var;
        System.out.println(var);
    }