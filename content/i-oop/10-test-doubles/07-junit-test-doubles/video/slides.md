---
type: "reveal"
hidden: true
---
<section>
    <img class="plain stretch" src="/cc410/images/13/410_13_mockito.png">
    <p class="imagecredit">Image Credit: <a href="https://site.mockito.org/">Mockito</a></p>
</section>
<section>
    <h3>Install in Gradle</h3>
    <pre><code class="java" style="font-size: 35px">dependencies {
    // Use JUnit Jupiter API for testing.
    testImplementation ..., 'org.mockito:mockito-inline:3.8.0',
    'org.mockito:mockito-junit-jupiter:3.8.0'<br>
    ...
}</code></pre>
</section>
<section>
    <h3>Add Mockito to Test Class</h3>
    <pre><code class="java stretch" style="font-size: 38px">import static org.junit.jupiter.api.Assertions.assertTrue;
import static org.mockito.Mockito.when;<br>
import org.junit.jupiter.api.Test;
import org.junit.jupiter.api.extension.ExtendWith;
import org.mockito.Mock;
import org.mockito.junit.jupiter.MockitoExtension;<br>
@ExtendWith(MockitoExtension.class)
public class UnitTestClass {
    // tests here
}</code></pre>
</section>
<section>
    <h3>Use Strict Stubs</h3>
    <pre><code class="java stretch" style="font-size: 38px">import static org.junit.jupiter.api.Assertions.assertTrue;
import static org.mockito.Mockito.when;<br>
import org.junit.jupiter.api.Test;
import org.mockito.Mock;
import org.mockito.junit.jupiter.MockitoSettings;
import org.mockito.quality.Strictness;<br>
@MockitoSettings(strictness = Strictness.STRICT_STUBS)
public class UnitTestClass {
    // tests here
}</code></pre>
</section>
<section>
    <h3>Creating Fake Objects</h3>
    <pre><code class="java stretch" style="font-size: 38px">@MockitoSettings(strictness = Strictness.STRICT_STUBS)
public class UnitTestClass {<br>
    @Mock
    Person mockPerson;
    @Mock
    Teacher mockTeacher;<br>
    public void testClassroomHasTeacher() {
        Classroom classroom = new Classroom()
        assertTrue(classroom.hasTeacher() == false);<br>
        classroom.addTeacher(mockTeacher);
        assertTrue(classroom.hasTeacher() == true);
    }
}</code></pre>
</section>
<section>
    <h3>Adding a Stub</h3>
    <pre><code class="java stretch" style="font-size: 31px">@MockitoSettings(strictness = Strictness.STRICT_STUBS)
public class ClassroomTest {<br>
    @Mock
    Person mockPerson;
    @Mock
    Teacher mockTeacher;<br>
    @Test
    public void testClassroomGetTeacherName() {
        // create a method stub for `getName`
        when(mockTeacher.getName()).thenReturn("Teacher Person");<br>
        Classroom classroom = new Classroom();
        classroom.addTeacher(mockTeacher);<br>
        // assert that the classroom returns the teacher's name
        assertTrue(classroom.getTeacherName().equals("Teacher Person"));
    }
}</code></pre>
</section>
<section>
    <h3>Static Classes</h3>
    <pre><code class="java stretch" style="font-size: 24px">@Test
public void testTeacherFailsMinimumAgeRequirement() {
    // Create mock static class
    try (MockedStatic<TeacherRules> mockTeacherRules = Mockito.mockStatic(TeacherRules.class)) {<br>
        // Create method stub for static class
        mockTeacherRules.when(() -> TeacherRules.getMinAge()).thenReturn(16);<br>
        // Create method stub for fake Teacher
        when(mockTeacher.getAge()).thenReturn(15);<br>
        // Test functionality
        Classroom classroom = new Classroom();
        assertThrows(IllegalArgumentException.class, () -> classroom.addTeacher(mockTeacher));
    }
}</code></pre>
</section>
