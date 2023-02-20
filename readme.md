```
from abaqus import * 
from abaqusConstants import * 
import regionToolset

vectors = [
            (98.0, 91.0, 33.0), (32.0, 64.0, 114.0), (94.0, 114.0, 78.0),
            (4.0, 100.0, 111.0), (82.0, 37.0, 114.0), (3.0, 51.0, 45.0),
            (61.0, 52.0, 76.0), (90.0, 30.0, 60.0), (82.0, 106.0, 114.0),
            (31.0, 100.0, 30.0), (40.0, 22.0, 30.0), (8.0, 6.0, 63.0),
            (40.0, 19.0, 94.0), (57.0, 68.0, 27.0), (32.0, 64.0, -5.0),
            (84.0, -5.0, 78.0), (123.0, 100.0, 111.0), (3.0, 100.0, -8.0),
            (123.0, 100.0, 111.0), (123.0, 100.0, -8.0), (3.0, 100.0, -8.0),
            (82.0, 37.0, -5.0), (123.0, 51.0, 45.0), (82.0, -12.0, 114.0),
            (82.0, 106.0, -5.0), (82.0, -12.0, 114.0), (82.0, -12.0, -5.0),
            (82.0, 106.0, -5.0), (128.0, 6.0, 63.0), (8.0, 126.0, 63.0),
            (8.0, 126.0, 63.0), (128.0, 126.0, 63.0), (128.0, 6.0, 63.0),
        ]
        
for x in range(0, x_boundary):
    for y in range(0, y_boundary):
        order_of_cell = y + (x) * (y_boundary)
        Sphere = "Sphere-" + str(order_of_cell)
        vector_index = y % 33
        order = y // 33
        vector_list = list(vectors[vector_index])
        if order >= 1 :
            vector_list[1] += 100
        if x >= 1 and y <= 32 :
            vector_list[0] += 100
        vectors[vector_index] = tuple(vector_list)
        a1.translate(instanceList=(Sphere, ), vector=vectors[vector_index])
        a1 = mdb.models['Model-1'].rootAssembly 
        if y + 1 == y_boundary:
            number_of_go_up = (y_boundary / 33) -1
            for k in range(0, vector_index + 1):
                vector_list = list(vectors[k])
                vector_list[1] -= (100 * number_of_go_up)
                vectors[k] = tuple(vector_list)
```
