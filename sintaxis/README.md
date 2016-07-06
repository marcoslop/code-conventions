# Sintaxis

### Sintaxis for Code Blocks

    if (condition){
        //Code
    }

    if (condition){
        //Code
    }else{
        //Code
    }

    while (condition){
        //Code
    }

    String value = method(param1, param2);

Note where the start bracket is set. The spaces should also be taken into account.

### Always use brackets in Ifs, whiles, fors, etc...

Brackets are mandatory, even if the following block is only a line.

Links related:

- [http://stackoverflow.com/questions/8020228/is-it-ok-if-i-omit-curly-braces-in-java](http://stackoverflow.com/questions/8020228/is-it-ok-if-i-omit-curly-braces-in-java)  
    (Personally I always include the brackets to reduce the possibility of confusion when reading or modifying the code.)

### Ternary operator

Should only be used if the condition and expresions are explained in a clear way. Should not be used when there are '&&'' or '||'.

Example of good use:

    double prize = boleto.getPrizePaid()!=null ? boleto.getPrizePaid() : boleto.getPrizeOriginal();

Example of bad use:

    double prize = (boleto.getPrizePaid()!=null && boleto.getPrizeOriginal()!=null) ? boleto.getPrizePaid() : boleto.getPrizeOriginal();


### Blank lines in code

Should not be used. 

Whenever a blank line is to be inserted, you should think: "why is this needed?"
Is it because you want to separate one block of lines of code from another because they do different things? Maybe this is a smell that tells you that the method is not using code of the same level of abstraction and should be refactored in other methods to be read in a clearer way.

### Comments

Whenever is possible avoid them.

If you are tempted to insert one comment, ask yourself if the code is not well programmed and could be avoided by refactoring the following lines into a new method with a verbose method name.

Example:

    BoletoIterator iterator = createIterator(50);
    while (iterator.hasNext()){
        Boleto boleto = iterator.nextBoleto();
        //For each boleto update some properties.
        boleto.setShared(boleto.isShared());
        boleto.setSharingReceived(boleto.isSharingReceived());
        if (boleto.isParticipacionPenya() && !Boleto.BoletoType.PARTICIPACION_PENYA.equals(boleto.getType())){
            boleto.setType(Boleto.BoletoType.PARTICIPACION_PENYA);
        }
    }
    

Can be updated to this:

    BoletoIterator iterator = createIterator(50);
    while (iterator.hasNext()){
        Boleto boleto = iterator.nextBoleto();
        updateBoletoProperties(boleto);
    }

    private void updateBoletoProperties (Boleto boleto){
        boleto.setShared(boleto.isShared());
        boleto.setSharingReceived(boleto.isSharingReceived());
        if (boleto.isParticipacionPenya() && !Boleto.BoletoType.PARTICIPACION_PENYA.equals(boleto.getType())){
            boleto.setType(Boleto.BoletoType.PARTICIPACION_PENYA);
        }
    }

There is an exception with comments in classes. If you think a comment in a class may be usefull, we are ok with it. Example:

    /**
     * Scheduler encargado de obtener y procesar las apuestas pendientes de ser enviadas a las administraciones.
     **/
    @Singleton
    public class ApuestasDeliverScheduler {


### Templates

You should disable the automatic code templates that add a comment in every new class created. For example:

    /**
    *  Created by marcoslop in 10/06/2016
    **/

This comments don´t contribute with anything interesting. If we want to know who created this file we can check it in the version control.
