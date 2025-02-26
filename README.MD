# Some useful algorithms in pure Cython - no dependencies

### Tested against Windows 10 / Python 3.11 / Anaconda

### pip install cythoncubicspline

### Cython and a C compiler must be installed!


``` py
from cythoncubicspline import (
    calculate_missing_coords,
    get_rectangle_coordinates_surface,
    get_circle_coordinates_surface,
    get_ellipse_coordinates_surface,
    bresenham_line,
    get_polygon_coordinates_surface,
    convex_hull,
    calculate_missing_coords_and_fill_all_holes,
    get_coords_of_line,
    logsplit,
    logspace,
    linspace,
    get_circle_coordinates,
    groupcoords_asc_desc,
    cubic_interp1d,
    difflist,
)

circle_coords = get_circle_coordinates(x=20, y=20, r=10)
print(f"{circle_coords=}")

```

----------------------------
``` py
rect_coords = get_rectangle_coordinates_surface(10, 10, 5, 5)
print(f"{rect_coords=}")
```

----------------------------
``` py
circle_surface_coords = get_circle_coordinates_surface(
    x_center=20, y_center=20, radius=10
)
print(f"{circle_surface_coords=}")
```

----------------------------
``` py
ellipse_coords = get_ellipse_coordinates_surface(0, 0, 10, 5)
print(f"{ellipse_coords}")
```

----------------------------
``` py
line_coords = bresenham_line(0, 0, 25, 5)
print(f"{line_coords=}")

```

----------------------------
``` py
polygon_coords = get_polygon_coordinates_surface(
    [
        (350, 100),
        (450, 450),
        (150, 400),
        (100, 200),
        (350, 100),
        (200, 300),
        (350, 350),
        (300, 200),
        (200, 300),
    ]
)
print(f"{polygon_coords=}")
```

----------------------------
``` pyhull_coords = convex_hull([(1, 1), (3, 2), (2, 3), (0, 0), (3, 3)])
print(hull_coords)

```

----------------------------
``` pycoordlist = [
    (12, 100),
    (9, 90),
    (10, 80),
    (9, 70),
    (7, 60),
    (5, 50),
    (6, 40),
    (5, 30),
    (4, 20),
    (4, 10),
    (3, 0),
    (3, 10),
    (5, 20),
    (3, 30),
    (7, 40),
    (7, 50),
    (7, 60),
    (9, 70),
    (11, 80),
    (12, 90),
    (11, 100),
    (7, 70),
    (7, 40),
    (4, 10),
]
result_groupcoords = groupcoords_asc_desc(coordlist, xtolerance=-2)
for x in result_groupcoords:
    print(x)
[(0, (12, 100))]
[(1, (9, 90)), (3, (9, 70))]
[(4, (7, 60))]
[(5, (5, 50)), (7, (5, 30))]
[(8, (4, 20)), (10, (3, 0)), (11, (3, 10)), (12, (5, 20))]
[
    (13, (3, 30)),
    (14, (7, 40)),
    (15, (7, 50)),
    (16, (7, 60)),
    (17, (9, 70)),
    (18, (11, 80)),
    (20, (11, 100)),
]
[(21, (7, 70)), (22, (7, 40))]
```

----------------------------
``` py
coords=[
    (160, 218),
    (133, 305),
    (109, 399),
    (128, 502),
    (120, 608),
    (107, 705),
    (106, 806),
    (174, 898),
    (325, 928),
    (399, 881),
    (444, 751),
    (474, 583),
    (479, 453),
    (496, 337),
    (545, 234),
    (670, 177),
    (796, 219),
    (910, 285),
    (951, 363),
    (972, 483),
    (991, 602),
    (1056, 744),
    (1137, 817),
    (1286, 877),
    (1419, 777),
    (1507, 603),
    (1504, 446),
    (1341, 282),
    (1218, 238),
    (1111, 233),
    (1010, 200),
    (888, 172),
    (715, 173),
    (595, 165),
    (487, 167),
    (367, 178),
    (283, 210),
    (216, 269),
    (172, 348),
    (151, 442),
    (171, 543),
    (224, 634),
    (254, 720),
    (323, 772),
    (443, 789),
    (562, 797),
    (680, 802),
    (802, 808),
    (929, 807),
    (1089, 826),
    (1220, 863),
    (1341, 902),
    (1300, 972),
    (1179, 981),
    (1019, 956),
    (845, 927),
    (694, 903),
    (514, 878),
    (361, 845),
    (269, 785),
    (203, 698),
    (170, 606),
    (197, 513),
    (272, 454),
    (366, 398),
    (475, 347),
    (661, 329),
    (863, 359),
    (1010, 358),
    (1211, 351),
    (1350, 308),
    (1449, 259),
    (1447, 178),
    (1302, 120),
    (1197, 114),
    (1062, 122),
    (908, 125),
    (797, 129),
    (699, 137),
]
calcalist = calculate_missing_coords(coordlist=coords, xtolerance=-2)
print(f"{calcalist=}")
calcalist = calculate_missing_coords_and_fill_all_holes(coordlist=coords, xtolerance=-2)
print(f"{calcalist=}")
# import matplotlib.pyplot as plt
# plt.plot(*zip(*calcalist))
# plt.show()
```

----------------------------
``` pylinecoords = get_coords_of_line(10, 20, 50, 70)
#import matplotlib.pyplot as plt
#plt.plot(*zip(*linecoords))
#plt.show()

```

----------------------------
``` pyfor l in logsplit(list(range(50))):
    print(l)
[0]
[1, 2]
[3, 4, 5]
[6, 7, 8, 9]
[10, 11, 12, 13, 14]
[15, 16, 17, 18, 19, 20]
[21, 22, 23, 24, 25, 26, 27]
[28, 29, 30, 31, 32, 33, 34, 35]
[36, 37, 38, 39, 40, 41, 42, 43, 44]
[45, 46, 47, 48, 49]
```

``` pyfor l in logspace(start=10, stop=100, num=20):
    print(l)
10.0
11.14684748713282
11.46139906526985
11.86222427300331
12.372985808857322
13.023836457655403
13.853199158847453
14.910035303051664
16.25673516559804
17.97280111369074
20.159541025162195
22.946048994588956
26.49682639749191
31.021493221811085
36.787162974681834
44.13421171659021
53.49637214714573
65.4263389959423
80.62839733163142
100.0
```

----------------------------
``` py
for l in linspace(start=10, stop=100, number=7, endpoint=True):
    print(l)
10.0
25.0
40.0
55.0
70.0
85.0
100.0
```

----------------------------
``` py
for q in difflist(list(range(1,20,3))):
    print(q)
3
3
3
3
3
3
```
