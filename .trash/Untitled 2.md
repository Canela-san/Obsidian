struct id* find_element (struct id* p, short v) {
for ( ; p != 0; p = p->next) {
if (p->val == v)
return p;
}
return 0;
}