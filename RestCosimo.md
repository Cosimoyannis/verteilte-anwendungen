Erstellen einer Rest Schnittstelle 

Projekte können erstellt werden und mit usern verbunden werden.
Es können mehrere Versionen erstellt und aufgerufen werden. 

{
    "name": {1,2},
    "user": {1,2},
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

    static private Map<ProjectJson> projects = new HashMap<>();

    @POST 
    @Consumes(MediaType.APPLICATION_JSON)
    @Produces("application/example")
    public createProject(ProjectJson json) {
         logger.info(json);
         UUID id = UUID.randomUUID();
         this.projects.put(id.toString(), json); // json speichern in Liste
         return id.toString();
    }

    @GET
    @Path("{id")
    @Produces(MediaType.APPLICATION_JSON))
    public String getProject(@PathParam("id") String id) {
        return projects.get(id);
    }

    @DELETE
    @Path("{id")
    public void delteProject(){
        projects.remove(id); 
    }

    @PUT 
    @Path("{id")
    public void putProject(){
        projects.put(id, json); 
    }

    
    
    
}




