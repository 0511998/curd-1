// Dependencies: jersey-container-servlet-core, jersey-server

import javax.ws.rs.*;
import javax.ws.rs.core.MediaType;
import javax.ws.rs.core.Response;
import java.util.HashMap;
import java.util.Map;

@Path("/students")
public class StudentResource {

    private static Map<Integer, Student> students = new HashMap<>();

    @GET
    @Path("/{id}")
    @Produces(MediaType.APPLICATION_JSON)
    public Response getStudent(@PathParam("id") int id) {
        Student student = students.get(id);
        if (student != null) {
            return Response.ok(student).build();
        } else {
            return Response.status(Response.Status.NOT_FOUND).build();
        }
    }

    @POST
    @Consumes(MediaType.APPLICATION_JSON)
    public Response addStudent(Student student) {
        students.put(student.getId(), student);
        return Response.status(Response.Status.CREATED).build();
    }

    @PUT
    @Path("/{id}")
    @Consumes(MediaType.APPLICATION_JSON)
    public Response updateStudent(@PathParam("id") int id, Student updatedStudent) {
        Student student = students.get(id);
        if (student != null) {
            student.setName(updatedStudent.getName());
            student.setAge(updatedStudent.getAge());
            return Response.ok().build();
        } else {
            return Response.status(Response.Status.NOT_FOUND).build();
        }
    }

    @DELETE
    @Path("/{id}")
    public Response deleteStudent(@PathParam("id") int id) {
        Student student = students.remove(id);
        if (student != null) {
            return Response.ok().build();
        } else {
            return Response.status(Response.Status.NOT_FOUND).build();
        }
    }
}
