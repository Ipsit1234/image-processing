def make_quads(points):
    all_quads = itertools.combinations(points,4)
    all_quads = [list(element) for element in all_quads]
    return list(all_quads)

def distance(point1,point2):
    x1,y1 = point1
    x2,y2 = point2
    dx = x1-x2
    dy = y1-y2
    return math.sqrt(dx**2+dy**2)

def mid_point(point1,point2):
    x1,y1 = point1
    x2,y2 = point2
    return ((x1+x2)/2,(y1+y2)/2)

def make_hashcodes(points):
    combs = itertools.combinations(points,2)
    combs = list(combs)
    max_dist = -1
    for i in combs:
        if distance(i[0],i[1]) > max_dist:
            max_dist = distance(i[0],i[1])
            A = i[0]
            B = i[1]
        else:
            pass

    for i in range(len(points)):
        if points[i] == A:
            del points[i]
            break
    for j in range(len(points)):
        if points[j] == B:
            del points[j]
            break
    C,D = points
    B1 = B.copy()
    C1 = C.copy()
    D1 = D.copy()
    
    for i in range(2):
        B1[i] = B[i] - A[i]
        C1[i] = C[i] - A[i]
        D1[i] = D[i] - A[i]
    
    theta1 = np.arctan(B1[1]/B1[0])
    theta = np.pi/4 - theta1
    rot_matrix = np.array([[np.cos(theta),-np.sin(theta)],[np.sin(theta),np.cos(theta)]])
    B1 = np.array([[B1[0]],[B1[1]]])
    C1 = np.array([[C1[0]],[C1[1]]])
    D1 = np.array([[D1[0]],[D1[1]]])
    D1 = np.dot(rot_matrix,D1)
    C1 = np.dot(rot_matrix,C1)
    
    ratio = math.sqrt(2)/distance(A,B)
    C1 = C1 * ratio
    D1 = D1 * ratio
    
    if D1[0] <= C1[0] and C1[0] + D1[0] <=1 :
        temp = D1
        D1 = C1
        C1 = temp
    elif C1[0] <= D1[0] and C1[0] + D1[0] <=1 :
        C1 = C1
        D1 = D1
    mp = [0.5,0.5]
    if distance(mp,C1) < max_dist/2 and distance(mp,D1) < max_dist/2:
        return [list(C1[0]),list(C1[1]),list(D1[0]),list(D1[1])]
    else:
        return 'failed'
