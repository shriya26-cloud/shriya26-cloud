INF = 999999
nV = 4
G = [[0, 2, INF, 9],
     [INF, 0, 7, 3],
     [3, INF, 0, 6],
     [INF, INF, 1, 0]]

def floyd(G):
    dist = list(map(lambda p: list(map(lambda q: q, p)), G))
    for r in range(nV):
        for p in range(nV):
            for q in range(nV):
                dist[p][q] = min(dist[p][q], dist[p][r] + dist[r][q])
    sol(dist)

def sol(dist):
    print("The following matrix shows the shortest distances between every pair of vertices:")
    for i in range(nV):
        for j in range(nV):
            if dist[i][j] == INF:
                print("%7s" % ("INF"), end=" ")
            else:
                print("%7d" % (dist[i][j]), end=" ")
        print()

floyd(G)
