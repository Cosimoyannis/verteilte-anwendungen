Erstellen einer Rest Schnittstelle 

Projekte können erstellt werden und mit usern verbunden werden.
Es können mehrere Versionen erstellt und aufgerufen werden. 

{
    "name"= {1,2},
    "user"= {1,2},
}



POST: v1/projects/{id wird automatisch erstellt}

GET: v1/projects/{id}

DELETE: v1/projects/{id}

PUT: v1/projects/{id}



START: mvn package
UM KOMPILIERTE PROJECT ZU SEHEN: ls target
BAUEN IN DEV MODE, LIVE ENTWICKLUNG: mvn compile quarkus:dev



@Path("/v1/projects")
public class ProjectRessource{

    @Inject
    Logger logger;

    @POST 
    @Consumes(MediaType.APPLICATION_JSON)
    public createProject(ProjectJson json) {
         logger.info(json);
    }

    @GET
    @Produces(MediaType.TEXT_PLAIN)
    public String getProject() {
        return "hello";
    }

    @DELETE
    public void delteProject(){

    }

    @PUT 
    public void putProject(){

    }

    
    
    
}